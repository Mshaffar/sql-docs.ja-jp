---
title: sp_helpreplfailovermode (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplfailovermode
- sp_helpreplfailovermode_TSQL
helpviewer_keywords:
- sp_helpreplfailovermode
ms.assetid: d1090e42-6840-4bf6-9aa9-327fd8987ec2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 93793b697ea2e59f4725cf61d2d3fcec4ebdf579
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824464"
---
# <a name="sp_helpreplfailovermode-transact-sql"></a>sp_helpreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクリプションの現在のフェールオーバー モードを表示します。 このストアド プロシージャは、任意のデータベース上のサブスクライバー側で実行されます。 フェールオーバーモードの詳細については、「[トランザクションレプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpreplfailovermode [ @publisher= ] 'publisher'   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]   
    [ , [ @failover_mode_id= ] 'failover_mode_id'OUTPUT]   
    [ , [ @failover_mode = ] 'failover_mode'OUTPUT]   
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'`このサブスクライバーの更新に参加しているパブリッシャーの名前を指定します。 *publisher*は**sysname**で、既定値はありません。 パブリッシャーは、既に発行用に構成されている必要があります。  
  
`[ @publisher_db = ] 'publisher_db'`パブリケーションデータベースの名前を指定します。 *publisher_db*は**sysname**であり、既定値はありません。  
  
`[ @publication = ] 'publication'`このサブスクライバーの更新に参加しているパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @failover_mode_id = ] 'failover_mode_id' OUTPUT`フェールオーバーモードの整数値を返します。これは**出力**パラメーターです。 *failover_mode_id*は**tinyint**で、既定値は**0**です。 即時更新の場合は**0** 、キュー更新の場合は**1**を返します。  
  
`[ @failover_mode = ] 'failover_mode' OUTPUT`サブスクライバーでデータ変更が行われるモードを返します。 *failover_mode*は**nvarchar (10)** で、既定値は NULL です。 は**出力**パラメーターです。  
  
|[値]|説明|  
|-----------|-----------------|  
|**すばやい**|即時更新: サブスクライバーで行われた更新は、2フェーズコミットプロトコル (2PC) を使用してパブリッシャーに直ちに反映されます。|  
|**queued**|キュー更新。サブスクライバーでの更新は、キューに格納されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpreplfailovermode**は、フェールオーバーとしてキュー更新を使用した即時更新が有効になっているスナップショットレプリケーションまたはトランザクションレプリケーションで、障害が発生した場合に使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_helpreplfailovermode**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_setreplfailovermode &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
