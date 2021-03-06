---
title: 統計のプロパティの表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql13.swb.statistics.details.f1
helpviewer_keywords:
- viewing statistics properties
- statistics [SQL Server], viewing properties
ms.assetid: 0eaa2101-006e-4015-9979-3468b50e0aaa
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 45c297ea29dbab974f72f4ecf69deb5c65f57bbb
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "72908013"
---
# <a name="view-statistics-properties"></a>統計のプロパティの表示
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のテーブルまたはインデックス付きビューについての、現在のクエリの最適化に関する統計を表示します。 統計オブジェクトには、統計に関するメタデータが含まれるヘッダー、統計オブジェクトの最初のキー列の値の分布が含まれるヒストグラム、および列間の相関関係を測定する密度ベクトルが格納されています。 ヒストグラムと密度ベクトルの詳細については、「[DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)」を参照してください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **統計のプロパティを表示するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 統計オブジェクトを表示するには、テーブルを所有しているか、固定サーバー ロール **sysadmin** 、固定データベース ロール **db_owner** 、または固定データベース ロール **db_ddladmin** のメンバーである必要があります。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-statistics-properties"></a>統計のプロパティを表示するには  
  
1.  **オブジェクト エクスプローラー**で、新しい統計を作成するデータベースをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[テーブル]** フォルダーを展開します。  
  
3.  統計のプロパティを表示するテーブルのプラス記号をクリックして展開します。  
  
4.  プラス記号をクリックして **[統計]** フォルダーを展開します。  
  
5.  プロパティを表示する統計オブジェクトを右クリックし、 **[プロパティ]** を選択します。  
  
6.  **[統計のプロパティ -** statistics_name _]_ ダイアログ ボックスの **[ページの選択]** ウィンドウで **[詳細]** を選択します。  
  
     **[統計のプロパティ -** statistics_name **]** ダイアログ ボックスの _[詳細]_ ページで次のプロパティが表示されます。  
  
     **テーブル名**  
     統計の対象となるテーブルの名前が表示されます。  
  
     **[統計名]**  
     統計情報が格納されるデータベース オブジェクトの名前が表示されます。  
  
     **[INDEX の統計 statistics_name]**  
     このテキスト ボックスは、統計オブジェクトから返されるプロパティを示します。 このプロパティは、統計ヘッダー、密度ベクトル、およびヒストグラムという 3 つのセクションに分かれています。  
  
     以下に、統計ヘッダーを指定した場合に結果セットに返される列を示します。  
  
     **Name**  
     統計オブジェクトの名前。  
  
     **更新**  
     統計情報が最後に更新された日付と時刻。  
  
     **行数**  
     統計情報が最後に更新された時点のテーブルまたはインデックス付きビューの行の総数。 統計がフィルター選択されている場合、またはフィルター選択されたインデックスに対応している場合は、行数がテーブルの行数よりも少なくなることがあります。  
  
     **[サンプリングされた行数]**  
     統計の計算時にサンプリングされた行の合計数。 Rows Sampled < Rows の場合、表示されるヒストグラムおよび密度の結果は、サンプリングされた行に基づいて推定されます。  
  
     **手順**  
     ヒストグラムの区間の数。 各区間の範囲には、上限の列値までの列値の範囲が含まれます。 ヒストグラムの区間は、統計の最初のキー列に基づいて定義されます。 区間の最大数は 200 です。  
  
     **[密度]**  
     ヒストグラムの境界値を除く、統計オブジェクトの最初のキー列のすべての値について、"1 / *distinct values* " として計算されます。 この密度の値はクエリ オプティマイザーでは使用されません。SQL Server 2008 より前のバージョンとの互換性を維持するために表示されます。  
  
     **[キーの平均の長さ]**  
     統計オブジェクトのすべてのキー列の、値ごとの平均バイト数。  
  
     **String Index**  
     Yes の場合は、統計オブジェクトに文字列の統計概要が含まれています。これにより、LIKE 演算子を使用するクエリ述語 (`WHERE ProductName LIKE '%Bike'` など) に対するカーディナリティの推定が向上します。 文字列の統計概要は、ヒストグラムとは別に格納されます。この統計は、統計オブジェクトの最初のキー列について、その型が **char**、 **varchar**、 **nchar**、 **nvarchar**、 **varchar(max)** 、 **nvarchar(max)** 、 **text**、 **ntext**である場合に作成されます。  
  
     **[フィルター式]**  
     統計オブジェクトに含まれるテーブル行のサブセットの述語。 NULL = フィルター選択されていない統計情報です。  
  
     **[フィルター処理なしの行数]**  
     フィルター式を適用する前のテーブル内の行の合計数。 [フィルター式] が NULL の場合、[フィルター処理なしの行数] は [行数] と同じになります。  
  
     以下に、密度ベクトルを指定した場合に結果セットに返される列を示します。  
  
     **[すべての密度]**  
     密度は "1 / *distinct values*" です。 結果には、統計オブジェクトの列の各プレフィックスに対する密度が、密度ごとに 1 行表示されます。 個別の値は、行および列プレフィックスごとの列値の個別のリストです。 たとえば、統計オブジェクトにキー列 (A, B, C) が含まれる場合、結果では列プレフィックス (A)、(A, B)、および (A, B, C) ごとに個別の値リストの密度が報告されます。 プレフィックス (A, B, C) を使用すると、これらの各リストは個別の値リスト (3, 5, 6)、(4, 4, 6)、(4, 5, 6)、(4, 5, 7) のようになります。 プレフィックス (A, B) を使用すると、同じ列値の個別の値リストが (3, 5)、(4, 4)、および (4, 5) になります。  
  
     **[平均の長さ]**  
     列プレフィックスの列値のリストを格納する平均の長さ (バイト単位)。 たとえば、リスト (3, 5, 6) の値ごとに 4 バイト必要な場合は、長さは 12 バイトになります。  
  
     **[列]**  
     [すべての密度] および [平均の長さ] を表示するプレフィックスの列の名前。  
  
     以下に、ヒストグラムを指定した場合に結果セットに返される列を示します。  
  
     **[RANGE_HI_KEY]**  
     ヒストグラム区間の上限の列値。 この列値はキー値とも呼ばれます。  
  
     **RANGE_ROWS**  
     ヒストグラム区間内 (上限は除く) に列値がある行の予測数。  
  
     **EQ_ROWS**  
     ヒストグラム区間の上限と列値が等しい行の予測数。  
  
     **DISTINCT_RANGE_ROWS**  
     ヒストグラム区間内 (上限は除く) にある個別の列値を持つ行の予測数。  
  
     **AVG_RANGE_ROWS**  
     ヒストグラム区間内 (上限は除く) にある重複する列値を持つ行の平均数 (DISTINCT_RANGE_ROWS > 0 の場合 RANGE_ROWS / DISTINCT_RANGE_ROWS)  
  
7.  **[OK]** をクリックします。  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-view-statistics-properties"></a>統計のプロパティを表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example displays all statistics information for the AK_Address_rowguid index of the Person.Address table.   
    DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);   
    GO  
    ```  
  
 詳細については、「[DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)」を参照してください。  
  
#### <a name="to-find-all-of-the-statistics-on-a-table-or-view"></a>テーブルまたはビューのすべての統計を見つけるには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Gets the following information: name and ID of the statistics, whether the statistics were created automatically or by the user, whether the statistics were created with the NORECOMPUTE option, and whether the statistics have a filter and, if so, what that filter is.  
    */  
    SELECT name AS statistics_name  
        ,stats_id  
        ,auto_created  
        ,user_created  
        ,no_recompute  
        ,has_filter  
        ,filter_definition  
    -- using the sys.stats catalog view  
    FROM sys.stats  
    -- for the Sales.SpecialOffer table  
    WHERE object_id = OBJECT_ID('Sales.SpecialOffer');  
    GO  
    ```  
  
 詳細については、「[sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)」を参照してください。  
  
  
