---
title: sp_helppeerresponses (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppeerresponses_TSQL
- sp_helppeerresponses
helpviewer_keywords:
- sp_helppeerresponses
ms.assetid: e55789d1-43fb-4a37-9e5e-60ccef122a5d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f9303801527b3154585034e1097623ce073fb91f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834403"
---
# <a name="sp_helppeerresponses-transact-sql"></a>sp_helppeerresponses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ピアツーピアレプリケーショントポロジの参加者から受信した特定の状態要求に対するすべての応答を返します。この要求は、トポロジ内のパブリッシュされたデータベースで[sp_helppeerrequests](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)を実行することによって開始されます。 このストアドプロシージャは、ピアツーピアレプリケーショントポロジに参加しているパブリッシャー側のパブリケーションデータベースで実行されます。 詳細については、「[ピア ツー ピア トランザクション レプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helppeerresponses [ @request_id = ] request_id  
```  
  
## <a name="arguments"></a>引数  
`[ @request_id = ] request_id`特定の状態要求の ID を指定します。 *request_id*は**int**,、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|状態要求の ID。|  
|**家**|**sysname**|応答を生成したピアの名前。|  
|**peer_db**|**sysname**|応答を生成したピアのデータベース名。|  
|**received_date**|**datetime**|要求元が送信先のピアから応答を受信した日付と時刻。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helppeerresponses**は、ピアツーピアトランザクションレプリケーションで使用されます。  
  
 **sp_helppeerresponses**プロシージャは、ピアツーピアトポロジでパブリッシュされたデータベースを復元する場合に使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_helppeerresponses**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_deletepeerrequesthistory &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
