---
title: dm_fts_index_keywords (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords
- sys.dm_fts_index_keywords
- sys.dm_fts_index_keywords_TSQL
- dm_fts_index_keywords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords dynamic management function
- full-text search [SQL Server], viewing keywords
- troubleshooting [SQL Server], full-text search
ms.assetid: fce7b2a1-7e74-4769-86a8-c77c7628decd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e2b5631443603ea111c3ba154726ec3e6b39e0df
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67900943"
---
# <a name="sysdm_fts_index_keywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたテーブルのフルテキスト インデックスのコンテンツに関する情報を返します。  
  
 **dm_fts_index_keywords**は動的管理関数です。  
  
> [!NOTE]  
>  下位レベルのフルテキストインデックス情報を表示するには、ドキュメントレベルで[dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)動的管理関数を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>引数  
 db_id ('*database_name*')  
 [DB_ID ()](../../t-sql/functions/db-id-transact-sql.md)関数の呼び出し。 この関数は、データベース名を受け取り、データベース ID を返します。この ID は、指定されたデータベースを検索するために使用**dm_fts_index_keywords ます。** 場合 *database_name* は省略すると、現在のデータベース ID が返されます。  
  
 object_id ('*table_name*')  
 [OBJECT_ID ()](../../t-sql/functions/object-id-transact-sql.md)関数の呼び出し。 この関数は、テーブル名を受け取り、検査するフルテキストインデックスが含まれているテーブルのテーブル ID を返します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**keyword**|**nvarchar (4000)**|フルテキストインデックス内に格納されているキーワードの16進数表現。<br /><br /> 注: 0 Xff は、ファイルまたはデータセットの末尾を示す特殊文字を表します。|  
|**display_term**|**nvarchar (4000)**|キーワードの人間が判読できる形式。 この形式は、16進数形式から派生します。<br /><br /> 注: 0 Xff の**display_term**値は、"ファイルの終わり" です。|  
|**column_id**|**int**|現在のキーワードがフルテキストインデックスを作成した列の ID。|  
|**document_count**|**int**|現在の用語を含むドキュメントまたは行の数。|  
  
## <a name="remarks"></a>Remarks  
 Dm_fts_index_keywords によって返される情報は、特に次の点を確認するのに役立ちます **。**  
  
-   キーワードがフルテキストインデックスの一部であるかどうか。  
  
-   特定のキーワードを含むドキュメントまたは行の数。  
  
-   フルテキストインデックスで最も一般的なキーワードは次のとおりです。  
  
    -   合計**document_count**と比較した各*keyword_value*の**Document_count** 。ドキュメント数は0xff です。  
  
    -   通常、一般的なキーワードは、ストップワードとして宣言するのに適している可能性があります。  
  
> [!NOTE]  
>  **Dm_fts_index_keywords**によって返される**document_count**は、 **Sys. dm_fts_index_keywords_by_document**または**CONTAINS**クエリによって返されたカウントよりも、特定のドキュメントに対して正確ではない可能性があります。 この潜在的な不正確さは1% 未満であると推定されます。 この不正確さは、インデックスフラグメント内の複数の行にわたって連続している場合や、同じ行に複数回出現する場合に、 **document_id**が2回カウントされる可能性があるために発生する可能性があります。 特定のドキュメントの正確な数を取得するには、 **dm_fts_index_keywords_by_document**または**CONTAINS**クエリを使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-displaying-high-level-full-text-index-content"></a>A. 上位レベルのフルテキストインデックスコンテンツの表示  
 次の例では、 `HumanResources.JobCandidate`テーブル内のフルテキストインデックスの上位レベルのコンテンツに関する情報を表示します。  
  
```  
SELECT * FROM sys.dm_fts_index_keywords(db_id('AdventureWorks2012'), object_id('HumanResources.JobCandidate'))  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のフルテキスト検索とセマンティック検索の動的管理ビューおよび関数](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
