---
title: DirectQuery モードでの DAX 数式の互換性 (SSAS 2014) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: de83cfa9-9ffe-4e24-9c74-96a3876cb4bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e588630b4bc9b2dd72e1fb54362b9b024c17bdb5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67343896"
---
# <a name="dax-formula-compatibility-in-directquery-mode-ssas-2014"></a>DirectQuery モードでの DAX 数式の互換性 (SSAS 2014)
Data Analysis Expression 言語 (DAX) を使用すると、Analysis Services テーブルモデル、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Excel ブックのデータモデル、および Power BI Desktop データモデルで使用するメジャーやその他のカスタム式を作成できます。 ほとんどの場合、これらの環境で作成するモデルは同じであり、同じメジャー、リレーションシップ、および Kpi などを使用できます。ただし、Analysis Services テーブルモデルを作成して DirectQuery モードで配置した場合は、使用できる数式にいくつかの制限があります。 このトピックでは、これらの違いの概要について説明します。 SQL Server 2014 Analysis Services tabulars モデルでサポートされていない機能を互換性レベル1100または1103と DirectQuery モードで一覧表示し、サポートされているが、異なる結果を返す可能性のある関数を示します。  
  
このトピックでは、*インメモリモデル*という用語を使用して、テーブルモデルを参照します。テーブルモデルは、表形式モードで実行されている Analysis Services サーバー上のメモリ内キャッシュされたデータを完全にホストします。 Directquery*モデル*は、directquery モードで作成または配置されたテーブルモデルを参照するために使用します。 DirectQuery モードの詳細については、「 [Directquery モード (SSAS テーブル)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)」を参照してください。  
  
  
## <a name="differences-between-in-memory-and-directquery-mode"></a><a name="bkmk_SemanticDifferences"></a>インメモリ モードと DirectQuery モードの違い  
DirectQuery モードで配置されたモデルでのクエリは、同じモデルがインメモリで配置されたときとは異なる結果を返す場合があります。 これは、DirectQuery では、データがリレーショナルデータストアから直接クエリされ、数式に必要な集計が、ストレージと計算に xVelocity メモリ内分析エンジン (VertiPaq) を使用するのではなく、関連するリレーショナルエンジンを使用して実行されるためです。  
  
たとえば、特定のリレーショナル データ ストアが数値、日付、null などを処理する方法に違いがあります。  
  
一方、DAX 言語は、Microsoft Excel での関数の動作をできる限り忠実にエミュレートするようになっています。 たとえば、null、空の文字列、ゼロ値を処理するときに、Excel では正確なデータ型に関係なく最善の結果を提供するようになっているため、xVelocity エンジンも同様に動作します。 ただし、テーブルモデルが DirectQuery モードで配置され、評価のためにリレーショナルデータソースに数式を渡す場合、データはリレーショナルデータソースのセマンティクスに従って処理される必要があります。この場合、通常は空の文字列と null を個別に処理する必要があります。 このため、同じ数式でも、キャッシュされたデータに対して評価されるときと、リレーショナル ストアから戻されたデータのみに対して評価されるときでは、異なる結果が返される可能性があります。  
  
また、一部の関数は、現在のコンテキストのデータをパラメーターとしてリレーショナルデータソースに送信する必要があるため、DirectQuery モードではまったく使用できません。 たとえば、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]ブック内のメジャーは、ブック内で使用できる日付範囲を参照するタイムインテリジェンス関数を使用することがよくあります。 このような数式は、一般に、DirectQuery モードでは使用できません。  
  
## <a name="semantic-differences"></a>セマンティックの相違  
このセクションでは、予想されるセマンティックの相違の種類の一覧を示し、関数の使用方法またはクエリの結果に適用される可能性のある制限について説明します。  
  
### <a name="comparisons"></a><a name="bkmk_Comparisons"></a>比較  
インメモリ モデルでの DAX は、異なるデータ型のスカラー値に解決される 2 つの式の比較をサポートします。 一方、DirectQuery モードで配置されるモデルはリレーショナル エンジンのデータ型と比較演算子を使用するので、異なる結果が返される場合があります。  
  
次の比較は、DirectQuery データ ソースでの計算で使用すると、常にエラーが返されます。  
  
-   数値データ型と任意の文字列データ型の比較  
  
-   数値データ型とブール値の比較  
  
-   任意の文字列データ型とブール値の比較  
  
一般に、DAX はインメモリ モデルでの方がデータ型の不一致に対して寛容であり、このセクションで説明するように、最大で 2 回は値の暗黙のキャストを試みます。 一方、DirectQuery モードのリレーショナル データ ストアに送信される数式の方が、リレーショナル エンジンの規則に従ってより厳密に評価され、失敗する可能性が高くなります。  
  
**文字列と数値の比較**  
例: `"2" < 3`  
  
数式は文字列と数値を比較します。 式は、DirectQuery モードでもインメモリ モデルでも **true** になります。  
  
インメモリ モデルでは、文字列としての数値が数値データ型に暗黙でキャストされて他の数値と比較されるため、結果は **true** です。 SQL も、数値データ型との比較のために、テキストの数値を数値として暗黙的にキャストします。  
  
これは、最初のバージョンのからの[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]動作の変更を表します。これは、テキスト "2" は常に任意の数値より大きいと見なされるため、 **false**を返します。  
  
**テキストとブール値の比較**  
例: `"VERDADERO" = TRUE`  
  
この式は、テキスト文字列とブール値を比較します。 一般に、DirectQuery またはインメモリ モデルの場合、文字列値とブール値の比較の結果はエラーになります。 この規則に対する唯一の例外は、文字列に単語 **true** または **false**が含まれる場合です。この場合は、ブール型への変換が行われ、比較が実行されて論理的な結果が返されます。  
  
**Null 値の比較**  
例: `EVALUATE ROW("X", BLANK() = BLANK())`  
  
この数式は、SQL で NULL に相当する値と NULL を比較します。 インメモリ モデルおよび DirectQuery モデルでは **true** が返されます。DirectQuery モデルでは、インメモリ モデルと同じ動作が保証されるように準備が行われます。  
  
Transact-SQL では NULL と NULL は等しくならないことに注意してください。 ただし、DAX では空白は別の空白と等しくなります。 この動作はすべてのインメモリ モデルについて同じです。 ほとんどの場合、DirectQuery モードは SQL Server のセマンティックを使用します。しかし、この場合はそうではなく、新しい NULL 比較動作が行われます。  
  
### <a name="casts"></a><a name="bkmk_Casts"></a>色合い  
  
DAX のようなキャスト関数はありませんが、多くの比較演算および算術演算では暗黙のキャストが実行されます。 比較演算または数理演算により、結果のデータ型が決まります。 たとえば、  
  
-   ブール値は、算術演算では数値として扱われるか (TRUE + 1 など)、ブール値の列に関数 MIN が適用されます。 NOT 演算も数値を返します。  
  
-   ブール値は、比較において、および EXACT、AND、OR、 &amp;&amp;、または || で使用されるときは、常に論理値として扱われます。  
  
**文字列からブールへのキャスト**  
インメモリモデルと DirectQuery モデルでは、キャストは、 **""** (空の文字列)、 **"true"**、 **"false"** の各文字列からのブール値にのみ許可されます。空の文字列が false 値にキャストされます。  
  
他のすべての文字列からブール データ型へのキャストはエラーになります。  
  
**文字列から日付/時刻へのキャスト**  
DirectQuery モードでは、文字列表現の日時から実際の **datetime** 値へのキャストは、SQL Server と同じように行われます。  
  
モデル内の[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]文字列から**datetime**データ型へのキャストを管理する規則の詳細については、「 [DAX 構文リファレンス](/dax/dax-syntax-reference)」を参照してください。
  
インメモリ データ ストアを使用するモデルで日付に対してサポートされるテキスト形式の範囲は、SQL Server でサポートされる日付の文字列形式より制限されます。 ただし、DAX では日付と時刻のカスタム形式がサポートされます。  
  
**文字列から他の非ブール値へのキャスト**  
文字列から非ブール値へのキャストの場合、DirectQuery モードは SQL Server と同じように動作します。 詳細については、「 [CAST および CONVERT &#40;Transact-SQL&#41;](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8)」を参照してください。  
  
**認められない数値から文字列へのキャスト**  
例: `CONCATENATE(102,",345")`  
  
数値から文字列へのキャストは SQL Server では認められません。  
  
この数式は表形式モデルおよび DirectQuery モードではエラーになりますが、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]では結果が生成されます。  
  
**DirectQuery での 2 試行キャストの非サポート**  
インメモリ モデルでは、通常、第 1 のキャストが失敗すると、第 2 のキャストが試みられます。 DirectQuery モードではこのようなことは行われません。  
  
例: `TODAY() + "13:14:15"`  
  
この式では、第 1 のパラメーターは **datetime** 型で、第 2 のパラメーターは **string**型です。 ただし、オペランドを結合するときのキャストの処理は異なります。 DAX は、 **string** から **double**への暗黙のキャストを実行します。 インメモリ モデルでは、数式エンジンは **double**への直接キャストを試み、それが失敗した場合は、文字列から **datetime**へのキャストを試みます。  
  
DirectQuery モードでは、 **string** から **double** への直接キャストだけが試みられます。 このキャストが失敗した場合、数式はエラーを返します。  
  
### <a name="math-functions-and-arithmetic-operations"></a><a name="bkmk_Math"></a>数学関数と算術演算  
基になっているデータ型または演算で適用できるキャストの違いにより、一部の数学関数は、DirectQuery モードでは異なる結果を返します。 また、前に説明した許可される値の範囲についての制限が、算術演算の結果に影響する場合があります。  
  
**加算の順序**  
一連の数値を加算する数式を作成する場合、インメモリ モデルでは数値の処理順序が DirectQuery モデルと異なる場合があります。  したがって、非常に大きい正の値および非常に大きい負の値がある場合、演算によってはエラーになる場合と結果が返される場合があります。  
  
**POWER 関数の使用**  
例: `POWER(-64, 1/3)`  
  
DirectQuery モードの POWER 関数では、分数の指数に対する基数として負の値を使用することはできません。 これは SQL Server の想定される動作です。  
  
インメモリ モデルでは、この数式からは -4 が返されます。  
  
**数値のオーバーフロー動作**  
Transact-SQL では、数値オーバーフローになる演算ではオーバーフロー エラーが返されます。一方、DirectQuery モードでは、オーバーフローになる数式でもエラーが発生します。  
  
ただし、同じ数式をインメモリ モデルで使用すると、8 バイトの整数が返されます。 これは、数式エンジンが数値オーバーフローのチェックを実行しないためです。  
  
**異なる結果を返すブランクの LOG 関数**  
SQL Server では、NULL と空白の処理が xVelocity エンジンとは異なります。 その結果、次の式は、DirectQuery モードではエラーを返しますが、インメモリモードでは無限大 (-inf) を返します。  
  
`EXAMPLE: LOG(blank())`  
  
同じ制限が、他の対数関数 LOG10 および LN にも適用されます。  
  
DAX での **blank** データ型の詳細については、「 [DAX 構文のリファレンス](/dax/dax-syntax-reference)」を参照してください。
  
**0 での除算とブランクでの除算**  
DirectQuery モードでは、ゼロ (0) による除算または BLANK による除算は常にエラーになります。 SQL Server は無限大の表記をサポートしていず、0 による除算の自然な結果は無限大なので、結果はエラーになります。 ただし、SQL Server は NULL による除算はサポートしており、結果は常に NULL になります。  
  
DirectQuery モードでは、どちらの種類の演算 (ゼロによる除算と NULL による除算) でもエラーを返します。  
  
Excel モデルおよび [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] モデルでも、ゼロによる除算ではエラーが返されます。 ブランクによる除算ではブランクが返されます。  
  
次の式はすべて、インメモリ モデルでは有効ですが、DirectQuery モードでは失敗します。  
  
`1/BLANK`  
  
`1/0`  
  
`0.0/BLANK`  
  
`0/0`  
  
式 `BLANK/BLANK` は特殊なケースであり、インメモリ モデルでも DirectQuery モードでも `BLANK` が返されます。  
  
### <a name="supported-numeric-and-date-time-ranges"></a><a name="bkmk_Ranges"></a>サポートされる数値および日付と時刻の範囲  
メモリ内[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]のおよびテーブルモデルの数式には、実数と日付に許容される最大値に関して、Excel と同じ制限が適用されます。 ただし、最大値が計算またはクエリから返される場合、または値の変換、キャスト、丸め、または切り捨てが行われる場合は、相違が発生することがあります。  
  
-   **Currency** 型と **Real** 型の値の乗算を行い、結果が最大許容値より大きい場合、DirectQuery モードではエラーは発生せず、NULL が返されます。  
  
-   インメモリ モデルでは、エラーは発生しませんが、最大値が返されます。  
  
一般に、Excel と SQL Server では許容される日付の範囲が異なるため、結果が一致することが保証されるのは、共通の日付範囲内の日付の場合だけです。これには、次の日付が含まれます。  
  
-   最も早い日付: 1990 年 3 月 1 日  
  
-   最も遅い日付: 9999 年 12 月 31 日  
  
数式で使用されるいずれかの日付がこの範囲内にない場合は、数式がエラーになるか、または結果が一致しません。  
  
**CEILING でサポートされる浮動小数点値**  
例: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`  
  
DAX の CEILING 関数に相当する Transact-SQL の関数は、大きさが 10^19 以下の値のみをサポートします。 原則として、浮動小数点値は **bigint**に格納できます。  
  
**範囲外の日付での Datepart 関数**  
DirectQuery モードでの結果とインメモリ モデルでの結果が一致することが保証されるのは、引数として使用される日付が有効な日付範囲内である場合だけです。 この条件が満たされない場合は、エラーが発生するか、または DirectQuery とインメモリ モードで数式から返される結果が異なります。  
  
例: `MONTH(0)` または `YEAR(0)`  
  
DirectQuery モードでは、式から返される値はそれぞれ 12 および 1899 です。  
  
インメモリ モデルでは、それぞれ 1 および 1900 が返されます。  
  
例:  `EOMONTH(0.0001, 1)`  
  
この式の結果は、パラメーターとして渡されるデータが有効な日付範囲内の場合にのみ一致します。  
  
例: `EOMONTH(blank(), blank())` または `EDATE(blank(), blank())`  
  
この式の結果は、DirectQuery モードでもインメモリ モードでも同じになります。  
  
**時刻値の切り捨て**  
例: `SECOND(1231.04097222222)`  
  
DirectQuery モードでは、結果は SQL Server の規則に従って切り捨てられ、式は 59 と評価されます。  
  
インメモリ モデルでは、途中の各演算で結果が丸められるため、式は 0 と評価されます。  
  
この値の計算方法の例を次に示します。  
  
1.  入力の小数部 (0.04097222222) に 24 が乗算されます。  
  
2.  結果の時間の値 (0.98333333328) に 60 が乗算されます。  
  
3.  結果の分の値は 58.9999999968 です。  
  
4.  分の値の小数部 (0.9999999968) に 60 が乗算されます。  
  
5.  結果の 2 番目の値 (59.999999808) が 60 に丸められます。  
  
6.  60 は 0 と等価です。  
  
**SQL の時間データ型はサポートされない**  
インメモリ モデルでは、SQL の新しい **Time** データ型の使用はサポートされません。 DirectQuery モードでは、このデータ型の列を参照する数式はエラーを返します。 時刻データ列をインメモリ モデルにインポートすることはできません。  
  
ただし、および[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]では、キャッシュされたモデルでは、エンジンが時刻値を許容されるデータ型にキャストし、数式から結果が返されることがあります。  
  
この動作は、日付列をパラメーターとして使用するすべての関数に影響します。  
  
### <a name="currency"></a><a name="bkmk_Currency"></a>通貨  
DirectQuery モードでは、算術演算の結果が **Currency**型の場合、値は次の範囲内である必要があります。  
  
-   最小: -922337203685477.5808  
  
-   最大: 922337203685477.5807  
  
**通貨データ型と REAL データ型の組み合わせ**  
例: `Currency sample 1`  
  
**Currency** 型と **Real** 型を乗算して結果が 9223372036854774784 (0x7ffffffffffffc00) より大きい場合、DirectQuery モードではエラーは発生しません。  
  
インメモリ モデルでは、結果の絶対値が 922337203685477.4784 より大きい場合、エラーが発生します。  
  
**演算の結果が範囲外の値**  
例: `Currency sample 2`  
  
2 つの通貨値の演算の結果が指定されている範囲外の値になる場合、インメモリ モデルではエラーが発生しますが、DirectQuery モデルでは発生しません。  
  
**通貨データ型と他のデータ型の組み合わせ**  
通貨値を他の数値型の値で除算した場合、結果が異なる場合があります。  
  
### <a name="aggregation-functions"></a><a name="bkmk_Aggregations"></a>集計関数  
1 行のテーブルに対する統計関数は異なる結果を返します。 空のテーブルに対する集計関数も、インメモリ モデルと DirectQuery モードでは動作が異なります。  
  
**1 行のテーブルに対する統計関数**  
引数として使用されるテーブルに 1 行しか含まれない場合、DirectQuery モードでは STDEV や VAR などの統計関数は NULL を返します。  
  
インメモリ モデルでは、1 行だけのテーブルに対して STDEV または VAR を使用する数式はゼロ除算エラーを返します。  
  
### <a name="text-functions"></a><a name="bkmk_Text"></a>文字列関数  
リレーショナル データ ストアでは Excel とは異なるテキスト データ型が提供されるので、文字列の検索やサブストリングの処理での結果が異なる場合があります。 文字列の長さも異なる場合があります。  
  
一般に、固定サイズの列を引数として使用する文字列操作関数は結果が異なる場合があります。  
  
また、SQL Server の一部のテキスト関数は、Excel では提供されていない追加引数をサポートします。 足りない引数が数式で必要な場合、インメモリ モデルでは異なる結果またはエラーが発生する可能性があります。  
  
**LEFT や RIGHT などを使用する文字を返す演算では正しい文字が返されますが、大文字と小文字の使用が異なったり、または結果を返さない場合があります。**  
例: `LEFT(["text"], 2)`  
  
DirectQuery モードでは、返される文字の大文字と小文字の使い分けは、データベースに格納されている文字と常にまったく同じです。 ただし、xVelocity エンジンでは、パフォーマンスの向上のため、値の圧縮およびインデックス作成に使用されるアルゴリズムが異なります。  
  
既定で使用される Latin1_General 照合順序では、大文字と小文字は区別されませんが、アクセントは区別されます。 したがって、小文字だけ、大文字だけ、または小文字と大文字の混合を使用する、同じテキスト文字列の複数のインスタンスが存在する場合、すべてのインスタンスが同じ文字列と見なされて、文字列の最初のインスタンスだけがインデックスに格納されます。 格納された文字列を使用するすべてのテキスト関数は、インデックス形式の指定された部分を取得します。 したがって、例の数式では、最初のインスタンスを入力として使用し、列全体に対して同じ値を返します。  
  
[テーブル モデルの文字列ストレージと照合順序](https://msdn.microsoft.com/8516f0ad-32ee-4688-a304-e705143642ca)  
  
この動作は、RIGHT、MID などの他のテキスト関数にも適用されます。  
  
**結果に影響を与える文字列の長さ**  
例: `SEARCH("within string", "sample target  text", 1, 1)`  
  
SEARCH 関数を使用して文字列を検索し、ターゲットの文字列が内部の文字列より長い場合、DirectQuery モードではエラーが発生します。  
  
インメモリ モデルでは、検索された文字列が返されますが、長さは &lt;内部のテキスト&gt;の長さに切り詰められます。  
  
例: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`  
  
置換文字列の長さが元の文字列の長さより長い場合、DirectQuery モードでは数式は NULL を返します。  
  
インメモリ モデルでは数式は Excel の動作に従い、元の文字列と置換文字列を結合して、CACalifornia を返します。  
  
**文字列の途中での暗黙の TRIM**  
例: `TRIM(" A sample sentence with leading white space")`  
  
DirectQuery モードでは、DAX の TRIM 関数は SQL ステートメント `LTRIM(RTRIM(<column>))`に変換されます。 この結果、先頭と末尾の空白文字だけが削除されます。  
  
一方、インメモリ モデルでは、Excel の動作に従って、同じ数式により文字列内の空白文字が削除されます。  
  
**LEN 関数を使用するときの暗黙的な RTRIM**  
例: `LEN('string_column')`  
  
SQL Server と同様に、DirectQuery モードでは、文字列の列の最後から空白文字が自動的に削除されます。つまり、暗黙的に RTRIM が実行されます。 したがって、LEN 関数を使用する数式は、文字列の末尾に空白文字がある場合に異なる値を返すことがあります。  
  
**インメモリでサポートされる SUBSTITUTE の追加パラメーター**  
例: `SUBSTITUTE([Title],"Doctor","Dr.")`  
  
例: `SUBSTITUTE([Title],"Doctor","Dr.", 2)`  
  
DirectQuery モードでは、この関数のパラメーターが 3 つ (列の参照、古いテキスト、新しいテキスト) あるバージョンだけを使用できます。 2 番目の数式を使用するとエラーが発生します。  
  
インメモリ モデルでは、省略可能な 4 番目のパラメーターを使用して、置換する文字列のインスタンス番号を指定できます。 たとえば、2 番目のインスタンスだけを置換できます。  
  
**REPT 操作の文字列長の制限**  
インメモリ モデルでは、REPT を使用する操作の結果として生成される文字列の長さは、32,767 文字未満でなければなりません。  
  
この制限は、DirectQuery モードでは適用されません。  
  
**文字の型によって異なる結果を返すサブストリング操作**  
例: `MID([col], 2, 5)`  
  
入力テキストが **varchar** または **nvarchar**の場合、数式の結果は常に同じになります。  
  
ただし、テキストが固定長文字で、 * &lt;num_chars&gt; *の値がターゲット文字列の長さよりも大きい場合、DirectQuery モードでは、結果の文字列の末尾に空白が追加されます。  
  
インメモリ モデルでは、結果は文字列の最後の文字で終了し、ブランクの埋め込みは行われません。  
  
## <a name="functions-supported-in-directquery-mode"></a><a name="bkmk_SupportedFunc"></a>DirectQuery モードでサポートされている関数  
DirectQuery モードでは次の DAX 関数を使用できますが、前のセクションで説明した制限が適用されます。  
  
**テキスト関数**  
  
CONCATENATE  
  
[FIND]  
  
LEFT  
  
LEN  
  
MID  
  
REPLACE  
  
REPT  
  
RIGHT  
  
SUBSTITUTE  
  
TRIM  
  
**統計関数**  
  
[COUNT]  
  
STDEV.P  
  
STDEV.S  
  
STDEVX.P  
  
STDEVX.S  
  
VAR.P  
  
VAR.S  
  
VARX.P  
  
VARX.S  
  
**日付/時刻関数**  
  
DATE  
  
EDATE  
  
EOMONTH  
  
DATE  
  
TIME  
  
SECOND  
  
**数学関数と算術関数**  
  
CEILING  
  
LN  
  
LOG  
  
LOG10  
  
POWER  
  
**DAX テーブルクエリ**  
  
DAX テーブル クエリを使用して DirectQuery モデルに対する数式を評価するときは、いくつかの制限があります。 DirectQuery では、ORDER BY 句で同じ列を 2 回参照することはできません。 同等の Transact-SQL ステートメントを作成できず、クエリは失敗します。  
  
インメモリ モデルでは、ORDER BY 句を繰り返しても結果に影響はありません。  
  
## <a name="functions-not-supported-in-directquery-mode"></a><a name="bkmk_NotSupportedFunc"></a>DirectQuery モードでサポートされていない関数  
一部の DAX 関数は、DirectQuery モードで配置されたモデルではサポートされません。 特定の関数がサポートされない理由は、次のいずれか、または組み合わせによります。  
  
-   基になるリレーショナル エンジンが、xVelocity エンジンによって実行されるものと同等の計算を実行できない。  
  
-   数式を同等の SQL 式に変換できない。  
  
-   変換された式およびその結果の計算のパフォーマンスが受け入れられない。  
  
次の DAX 関数は、DirectQuery モデルでは使用できません。  
  
**パス関数**  
  
PATH  
  
PATHCONTAINS  
  
PATHITEM  
  
PATHITEMREVERSE  
  
PATHLENGTH  
  
**その他の関数**  
  
COUNTBLANK  
  
FIXED  
  
FORMAT  
  
RAND  
  
RANDBETWEEN  
  
**タイム インテリジェンス関数: 開始日と終了日**  
  
DATESQTD  
  
DATESYTD  
  
DATESMTD  
  
DATESQTD  
  
DATESINPERIOD  
  
TOTALMTD  
  
TOTALQTD  
  
TOTALYTD  
  
DATESINPERIOD  
  
SAMEPERIODLASTYEAR  
  
PARALLELPERIOD  
  
**タイムインテリジェンス関数: 残高**  
  
OPENINGBALANCEMONTH  
  
OPENINGBALANCEQUARTER  
  
OPENINGBALANCEYEAR  
  
CLOSINGBALANCEMONTH  
  
CLOSINGBALANCEQUARTER  
  
CLOSINGBALANCEYEAR  
  
**タイム インテリジェンス関数: 前の期間および次の期間**  
  
PREVIOUSDAY  
  
PREVIOUSMONTH  
  
PREVIOUSQUARTER  
  
PREVIOUSYEAR  
  
NEXTDAY  
  
NEXTMONTH  
  
NEXTQUARTER  
  
NEXTYEAR  
  
**タイム インテリジェンス関数: 期間および期間に対する計算**  
  
STARTOFMONTH  
  
STARTOFQUARTER  
  
STARTOFYEAR  
  
ENDOFMONTH  
  
ENDOFQUARTER  
  
ENDOFYEAR  
  
FIRSTDATE  
  
LASTDATE  
  
[DATEADD]  
  
## <a name="see-also"></a>関連項目  
[DirectQuery モード (SSAS テーブル)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)  
  

