---
title: 共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d1d7bc71-f0e9-4ce5-b3ad-6fee54388a31
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 644fa33aa0a9fd8bd51521270cfb89636ac63791
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78173201"
---
# <a name="create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs"></a>共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)
  データセットを作成する際は、1 つのレポートに使用する埋め込みデータセットか、レポート サーバーに保存して複数のレポートに使用する共有データセットを作成することができます。 データセットを作成するには、埋め込みデータ ソースまたは共有データ ソースが存在する必要があります。

 レポート ビルダーを使用して、次の作業を行います。

-   データセットのデザイン ビューで共有データセットを作成します。 共有データセットには、パブリッシュされた共有データ ソースを使用する必要があります。

-   レポートのデザイン ビューで、埋め込みのデータセットを作成します。

-   レポート サーバーまたは SharePoint サイトにデータセットを直接保存します。

 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、レポート デザイナーを使用して、次の作業を行います。

1.  ソリューション エクスプローラーで共有データセットを作成します。 共有データセットには、ソリューション エクスプローラーの [共有データ ソース] フォルダーのデータ ソースを使用する必要があります。

2.  レポート データ ペインで、埋め込みデータセットを作成します。

3.  必要に応じて、共有データセットと共有データ ソースをレポートと一緒に配置します。 アイテムの種類ごとに、プロジェクトのプロパティを使用して、レポート サーバーまたは SharePoint サイト上のフォルダーへのパスを指定します。

 詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-open-report-builder-and-create-a-shared-dataset"></a>レポート ビルダーを開き、共有データセットを作成するには

1.  レポート ビルダーを開きます。 次の図のように、 **[新しいレポートまたはデータセット]** ペインが開きます。

     ![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")

    > [!NOTE]
    >  **[新しいレポートまたはデータセット]** ペインが表示されない場合は、レポート ビルダーのボタンの **[新規作成]** をクリックします。

2.  左側のペインの **[データセットを作成する]** にある **[共有データセット]** をクリックします。

3.  右側のペインで、 **[参照]** をクリックしてレポート サーバーから共有データ ソースを選択し、 **[作成]** をクリックします。 共有データ ソースに関連付けられたクエリ デザイナーが開きます。

4.  クエリ デザイナーで、データセットに含めるフィールドを指定します。

5.  [**実行**] (**!**) をクリックしてクエリを実行します。

6.  **レポート ビルダー** のボタンの **[保存]** または **[名前を付けて保存]** をクリックして、共有データセットをレポート サーバーに保存します。

7.  レポート ビルダーを終了するには、 **[レポート ビルダー]** をクリックして、 **[レポート ビルダーの終了]** をクリックします。 レポートを使用するには、 **[レポート ビルダー]** をクリックして、 **[新規作成]** または **[開く]** をクリックします。

### <a name="to-set-query-parameter-options"></a>クエリ パラメーター オプションを設定するには

1.  レポート ビルダーを開きます。

2.  **[開く]** をクリックします。

3.  レポート サーバーを参照して共有データ ソースのフォルダーを選択します。

4.  **[アイテムの種類]** で、ドロップダウン リストの [データセット (*.rsd)] をクリックします。

5.  共有データセットを選択し、 **[開く]** をクリックします。 関連付けられているクエリ デザイナーが開きます。

6.  リボンの **[データセットのプロパティ]** をクリックします。

7.  **[パラメーター]** をクリックします。 このページで、定数または式に既定値を設定し、パラメーターを読み取り専用、Null 値許容、または **[クエリから省略]** としてマークします。 詳細については、「[[パラメーター] ([データセットのプロパティ] ダイアログ ボックス) &#40;レポート ビルダー&#41;](../dataset-properties-dialog-box-parameters-report-builder.md)」を参照してください。

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]


### <a name="to-create-a-dataset-from-a-sql-server-relational-database"></a>SQL Server リレーショナル データベースからデータセットを作成するには

1.  レポート データ ペインでデータ ソース名を右クリックし、 **[データセットの追加]** をクリックします。 **[データセットのプロパティ]** ダイアログ ボックスの **[クエリ]** ページが表示されます。

2.  **[名前]** にデータセットの名前を入力するか、既定の名前をそのまま使用します。

    > [!NOTE]
    >  データセット名は、レポート内部で使用されます。 判断しやすいように、データセットには、クエリが返すデータがわかるような名前を付けることをお勧めします。

3.  **[データ ソース]** で既存の共有データ ソースの名前を参照して選択するか、 **[新規作成]** をクリックして新しい埋め込みデータ ソースを作成します。

4.  **[クエリの種類]** オプションを選択します。 オプションは、データ ソースの種類によって異なります。

    -   データ ソースのクエリ言語を使用したクエリを作成するには、 **[Text]** を選択します。

    -   リレーショナル データベース テーブルのすべてのフィールドを取得するには、 **[Table]** を選択します。

    -   名前を指定してストアド プロシージャを実行するには、 **[ストアド プロシージャ]** を選択します。

5.  **[クエリ]** には、クエリ、ストアド プロシージャ、またはテーブル名を入力します。 あるいは、 **[クエリ デザイナー]** をクリックしてグラフィカルまたはテキストベースのクエリ デザイナー ツールを開くか、 **[インポート]** をクリックして既存のレポートからクエリをインポートします。

     ただし、データ ソースでクエリを実行することによってしか、クエリによって指定されたフィールド コレクションを決定できない場合もあります。 たとえば、ストアド プロシージャは結果セットのフィールドの変数セットを返す場合があります。 **[フィールドの更新]** をクリックしてデータ ソースでクエリを実行し、レポート データ ペインのデータセット フィールド コレクションを設定するのに必要なフィールド名を取得します。 **[データセットのプロパティ]** ダイアログ ボックスを閉じると、フィールド コレクションがデータセット ノードの下に表示されます。

6.  **[タイムアウト]** には、レポート サーバーがデータベースからの応答を待機する秒数を入力します。 既定値は 0 秒です。 クエリ タイムアウト値が 0 秒の場合は、クエリはタイムアウトしません。

7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     データセットとそのフィールド コレクションがレポート データ ペインのデータ ソース ノードの下に表示されます。

## <a name="see-also"></a>参照
 [レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと ssrs&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [データセットフィールドコレクション &#40;レポートビルダーと Ssrs&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [クエリデザイナー &#40;](../query-designers-report-builder.md)レポートビルダー&#41;レポートビルダーと Ssrs &#40;[の](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)[データ接続、データソース、および接続文字列レポートビルダー&#41;と ssrs レポートビルダーのデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md) [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md) [をレポートに追加](report-datasets-ssrs.md)&#40;


