---
title: sp_adddistributor (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributor
- sp_adddistributor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adddistributor
ms.assetid: 35415502-68d0-40f6-993c-180e50004f1e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 45088122cfb6824598aaf40486264d41216d3c39
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "68771319"
---
# <a name="sp_adddistributor-transact-sql"></a>sp_adddistributor (Transact-sql)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  は、(存在しない場合は) このテーブルにエントリを作成し、サーバーエントリをディストリビューターとしてマークし、プロパティ情報を格納[します。](../../relational-databases/system-compatibility-views/sys-sysservers-transact-sql.md) このストアドプロシージャは、ディストリビューター側で master データベースに対して実行され、サーバーをディストリビューターとして登録してマークします。 リモート ディストリビューターの場合、このストアド プロシージャは、master データベースからパブリッシャー側でも実行され、リモート ディストリビューターを登録します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adddistributor [ @distributor= ] 'distributor'   
    [ , [ @heartbeat_interval= ] heartbeat_interval ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @from_scripting= ] from_scripting ]  
```  
  
## <a name="arguments"></a>引数  
`[ @distributor = ] 'distributor'`ディストリビューションサーバーの名前を指定します。 *ディストリビューター*は**sysname**,、既定値はありません。 このパラメーターは、リモート ディストリビューターを設定する場合にのみ使用します。 このメソッドは、ディストリビューターのプロパティのエントリを msdb. に追加します。 **MSdistributor**テーブル。  
  
`[ @heartbeat_interval = ] heartbeat_interval`エージェントが進行状況メッセージをログに記録しなくてもよい最大時間を分単位で指定します。 *heartbeat_interval*は**int**,、既定値は10分です。 この間隔で実行され、実行されているレプリケーションエージェントの状態を確認する SQL Server エージェントジョブが作成されます。  
  
`[ @password = ] 'password']`**Distributor_admin**ログインのパスワードを入力します。 *パスワード*は**sysname**,、既定値は NULL です。 NULL または空の文字列の場合、パスワードはランダムな値にリセットされます。 パスワードは最初のリモート ディストリビューターを追加するときに構成する必要があります。 **distributor_admin**ログインと*パスワード*は、ローカル接続を含む*ディストリビューター* RPC 接続に使用されるリンクサーバーエントリ用に格納されます。 *ディストリビューター*がローカルの場合、 **distributor_admin**のパスワードは新しい値に設定されます。 リモートディストリビューターを持つパブリッシャーの場合、パブリッシャーとディストリビューターの両方で**sp_adddistributor**を実行するときに、 *password*に同じ値を指定する必要があります。 [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md)を使用して、ディストリビューターのパスワードを変更できます。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_adddistributor**は、スナップショットレプリケーション、トランザクションレプリケーション、およびマージレプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistributor-transa_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_adddistributor**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [パブリッシングおよびディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributor_property &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)  
  
  
