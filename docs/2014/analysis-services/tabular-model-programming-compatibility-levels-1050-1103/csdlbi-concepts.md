---
title: CSDLBI の概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 2fbdf621-a94d-4a55-a088-3d56d65016ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a51393748d47159cfc4cf6bf8bd25e50307cfb7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "79525443"
---
# <a name="csdlbi-concepts"></a>CSDLBI の概念
  BI 注釈付き概念スキーマ定義言語 (CSDLBI) は、さまざまなデータセットにプログラムでアクセスしてクエリやエクスポートを実行できるように各種のデータを抽象的に表す、Entity Data Framework に基づく言語です。 CSDLBI はリッチ形式でデータ ドリブンのレポートとアプリケーションをサポートしているため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して作成されたデータ モデルを表すために CSDLBI が使用されます。  
  
 このセクションでは、CSDLBI 表現と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ モデルをマップする方法 (テーブルと多次元の両方) を、各モデルの種類の例と共に説明します。  
  
 これらの概念を示すために、Codeplex から入手できる AdventureWorks サンプル データベースの例を使用しています。 サンプルの詳細については、「 [SQL Server のための Adventure Works サンプル](https://go.microsoft.com/fwlink/?linkID=220093)」を参照してください。  
  
## <a name="structure-of-a-tabular-model-in-csdlbi"></a>CSDLBI のテーブル モデルの構造  
 レポート モデルとそのデータを記述する CSDLBI ドキュメントでは、最初に xsd ステートメントを記述し、その後にモデルの定義を記述します。  
  
 モデルは名前空間として定義されます。主なエンティティ、アソシエーション、およびプロパティを次に示します。  
  
-   `EntityContainer` は、モデルのテーブルの一覧を示します。  
  
-   各テーブルは、`EntityContainer` で  `EntitySet` として示されます。  
  
-   2 つのテーブル間の各リレーションシップは、リレーションシップのエンド ポイントとロールを定義する `AssociationSet` として記述されます。  
  
-   `EntityType` 要素は、BISM 向けに拡張されており、テーブルやその列に関する追加情報を提供できるようになっています。これには、並べ替えや表示の目的で使用されるプロパティが含まれます。  
  
-   `Measure` 要素は、モデルで使用できる計算を定義します。 新しい `KPI` 要素を使用すると、一連の特殊な表示属性を追加することでメジャーを KPI に変換できます。  
  
-   パースペクティブの表現はありません。 パースペクティブに含まれていない列やテーブルが CSDL にある場合、`Hidden` 属性のフラグが設定されます。  
  
### <a name="entities-entitysets-and-entitytypes"></a>Entity、EntitySet、および Entitytype  
 Entity Data Framework のエンティティの表記が拡張され、データ モデルの列やテーブルを表現できるようになっています。 次の例は、テーブルを 3 つだけ含む単純なモデルの `EntitySet` 要素の記述部分を抜粋したものです。  
  
```  
<EntityContainer Name="SimpleModel">  
<EntitySet Name="DimCustomer"EntityType="SimpleModel.DimCustomer">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimDate" EntityType="SimpleModel.DimDate">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimGeography" EntityType="SimpleModel.DimGeography">  
     <bi:EntitySet />  
   </EntitySet> />  
  
```  
  
 `EntitySet` には、テーブルの列やデータに関する情報はありません。 列とそのプロパティの詳細な記述は、EntityType 要素で提供されます。  
  
 各エンティティ (テーブル) の `EntitySet` 要素には、キー列、列のデータ型と長さ、NULL 値を許容するかどうか、並べ替えの動作など、詳細を定義する一連のプロパティが含まれます。 たとえば、次の CSDL は、Customer テーブルの 3 つの列の記述部分を抜粋したものです。 最初の列は、モデルの内部で使用される特殊な非表示の列です。  
  
```  
<EntityType Name="Customer">  
  <Key>  
     <PropertyRef Name="RowNumber" />  
  </Key>  
    <Property Name="RowNumber" Type="Int64" Nullable="false">  
     <bi:Property Hidden="true" Contents="RowNumber"  
       Stability="RowNumber" />  
    </Property>  
    <Property Name="CustomerKey" Type="Int64" Nullable="false">  
      <bi:Property />  
    </Property>  
     <Property Name="FirstName" Type="String" MaxLength="Max" FixedLength="false">  
       <bi:Property />  
      </Property>  
  
```  
  
 生成される CSDLBI ドキュメントのサイズを制限するために、エンティティで複数回使用されるプロパティは、既存のプロパティへの参照で指定されます。これにより、`EntityType` には、各プロパティを 1 回だけ指定すれば済みます。 クライアント アプリケーションでは、`EntityType` に一致する `OriginEntityType` を検出することでプロパティの値を取得できます。  
  
### <a name="relationships"></a>リレーションシップ  
 Entity Data Framework では、リレーションシップはエンティティ間の*アソシエーション*として定義されます。  
  
 アソシエーションには必ず 2 つのエンド ポイントがあり、それぞれがテーブルのフィールドまたは列を参照します。 したがって、リレーションシップのエンド ポイントが異なれば、2 つのテーブル間に複数のリレーションシップを定義することができます。 アソシエーションのエンド ポイントにはロール名が割り当てられます。このロール名は、データ モデルのコンテキストにおけるアソシエーションの用途を示します。 たとえば、Orders テーブルの顧客 ID に関連付けられている顧客 ID に適用されている場合、ロール名の例として**ShipTo**が使用されることがあります。  
  
 モデルの CSDLBI 表現にはアソシエーションの属性も含まれており、アソシエーションの*複数要素*の接続性の観点からエンティティが相互にマップされる方法を決定します。 複数要素の接続性は、テーブル間のリレーションシップのエンド ポイントの属性または列がリレーションシップの "一" 側か "多" 側かを示します。 一対一のリレーションシップを表す値はありません。 CSDLBI 注釈でサポートされる複数要素の接続性の値は、エンティティが他のエンティティと関連付けられていないことを示す 0 と、一対一のリレーションシップまたは一対多のリレーションシップであることを示す 0..1 です。  
  
 次のサンプルは、列 DateAlternateKey で結合された Date および ProductInventory という 2 つのテーブルのリレーションシップの CSDLBI 出力を示しています。 既定では、`AssociationSet` の名前は、リレーションシップに関係する列の完全修飾名になります。 ただし、モデルのデザイン時にこの動作を変更すれば、別の名前付け形式を使用できます。  
  
```  
<AssociationSet Name="ProductInventory_Date_DateKey" Association="Model.ProductInventory_Date_DateKey">  
              <End EntitySet="ProductInventory" />  
              <End EntitySet="Date" />  
              <bi:AssociationSet />  
            </AssociationSet>  
  
```  
  
### <a name="visualization-and-navigation-properties"></a>視覚化とナビゲーションプロパティ  
 CSDLBI 注釈で重要なものに、レポート層での表示を定義するためのプロパティと、エンティティ間のリレーションシップをナビゲートするためのプロパティがあります。 通常、データ モデルを作成する際に、データの順序やグループ化の方法を制御したり既定値を決めたりすることはそれほど重要視されません。これは、順序などの表示に関する詳細はクライアント アプリケーションで指定されると想定されるためです。 ただし、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のテーブル モデルは [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポート クライアントと統合できる設計になっており、レポート デザイン画面でのデータ モデルのエンティティの表示をサポートするプロパティと属性が用意されています。  
  
 視覚化についての拡張機能には、数値データで使用する既定の集計を指定するための属性、テキスト フィールドが画像の URL を指すことを示すための属性、現在のフィールドの並べ替えに使用するフィールドを指定するための属性などがあります。  
  
### <a name="name-properties-and-naming-conventions"></a>名前のプロパティと名前付け規則  
 CSDLBI スキーマでは、キーとして使用できる一意の名前と識別子を各エンティティに割り当てるように規定されています。 また、一部のエンティティには、表示目的で使用されるキャプションや、エンティティの使用場所によって変化するコンテキスト名を指定できます。  
  
 `Documentation` 要素を使用すると、レポートの設計者は、ビジネス ユーザーがデータの意味を理解できるようにエンティティの説明を記述することができます。 また、一部のエンティティでは、1 つ以上の `Annotation` 属性を使用して、アプリケーションやクライアントで使用できる追加のメタデータを提供できます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ツールでモデルを生成すると、オブジェクトの名前付けと名前の一意性に関する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の規則に従ってオブジェクトの名前が作成されます。 ただし、CSDLBI は Entity Data Framework (EDF) に基づくため、C# の識別子に関する規則に従って名前を付ける必要があります。そのため、モデルの CSDLBI 出力をサーバーで作成するときに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のスキーマ内で使用されている名前が取得され、EDF の要件を満たす新しいオブジェクト名が自動的に作成されます。 次の表に、新しい名前が生成されるときの処理を示します。  
  
|ルール|アクション|  
|----------|------------|  
|禁止されている文字を使用しない|禁止されている文字は、アンダースコアに置き換えられます。|  
|名前は一意でなければならない|同じ文字列が 2 つある場合は、一意にするために、どちらかにアンダースコアと数値が追加されます。|  
  
> [!WARNING]  
>  キャプションと修飾子の両方に翻訳があります。特定の言語では、どちらか一方だけの場合もあります。 つまり、修飾子と名前または修飾子とキャプションを連結した場合、文字列が 2 種類の言語で示されることがあります。  
  
## <a name="additions-to-support-multidimensional-models"></a>多次元モデルをサポートするための追加事項  
 CSDLBI 注釈の Version 1.0 ではテーブル モデルのみがサポートされていました。 Version 1.1 では、従来の BI 開発ツールを使用して作成された多次元モデル (OLAP キューブ) もサポートされます。 その結果、多次元モデルに XML 要求を実行して、レポートで使用するためのモデルの CSDLBI 定義を受信できます。  
  
 **キューブ:** SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]表形式データベースには、1つのモードのみを含めることができます。 一方、多次元データベースには複数のキューブを含めることができ、各データベースは既定のキューブに関連付けられます。 したがって、XML 要求を多次元サーバーに対して実行する場合は、キューブを指定する必要があり、キューブを指定しないと、既定のキューブに対する XML が返されます。  
  
 その場合、キューブの表現はテーブル モデル データベースによく似ています。 キューブ名とキューブが、表形式のデータベース名とデータベース識別子に対応します。  
  
 **ディメンション:** ディメンションは、列とプロパティを持つエンティティ (テーブル) として CSDLBI で表されます。 パースペクティブに含まれていない場合でも、モデルに含まれるディメンションは、`Hidden` とマークされて CSDL 出力で表現されます。  
  
 **パースペクティブ:** クライアントは、個々のパースペクティブに対して CSDL を要求できます。 詳細については、「 [DISCOVER_CSDL_METADATA 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)」を参照してください。  
  
 **階層:** 階層はサポートされており、CSDLBI では一連のレベルとして表されます。  
  
 **メンバー:** 既定のメンバーのサポートが追加され、既定値が CSDLBI 出力に自動的に追加されました。  
  
 **計算されるメンバー:** 多次元モデルでは、1つの real メンバーを持つ**すべて**の子の計算されるメンバーがサポートされます。  
  
 **ディメンションの属性:** CSDLBI 出力では、ディメンション属性がサポートされており、自動的に集計不可としてマークされます。  
  
 **Kpi:** Kpi は CSDLBI バージョン1.1 でサポートされていましたが、表現が変更されました。 以前の KPI はメジャーのプロパティでした。 バージョン1.1 では、KPI 要素をメジャーに追加できます。  
  
 **新しいプロパティ:** DirectQuery モデルをサポートするために追加の属性が追加されました。  
  
 **制限事項:** セルのセキュリティはサポートされていません。  
  
## <a name="see-also"></a>参照  
 [ビジネス インテリジェンス向けの CSDL 注釈 (CSDLBI)](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
  
