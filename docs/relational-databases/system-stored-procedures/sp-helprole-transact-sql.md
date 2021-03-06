---
title: sp_helprole (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helprole_TSQL
- sp_helprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprole
ms.assetid: b023103f-ccf3-44e2-b418-4be9bdd49f4a
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 674da069c1c47c9e577327e9482add64353de881
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832626"
---
# <a name="sp_helprole-transact-sql"></a>sp_helprole (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内のロールに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helprole [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @rolename = ] 'role'`現在のデータベース内のロールの名前を指定します。 *role*の部分は**sysname**で、既定値は NULL です。 *ロール*は現在のデータベースに存在している必要があります。 *Role*が指定されていない場合は、現在のデータベース内のすべてのロールに関する情報が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**RoleName**|**sysname**|現在のデータベース内のロールの名前。|  
|**RoleId**|**smallint**|**RoleName**の ID。|  
|**IsAppRole**|**int**|0 = **RoleName**はアプリケーションロールではありません。<br /><br /> 1 = **RoleName**はアプリケーションロールです。|  
  
## <a name="remarks"></a>解説  
 ロールに関連付けられている権限を表示するには、 **sp_helprotect**を使用します。 データベースロールのメンバーを表示するには、 **sp_helprolemember**を使用します。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次のクエリでは、現在のデータベース内のすべてのロールが返されます。  
  
```  
EXEC sp_helprole  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [サーバーレベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [データベースレベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md)   
 [sp_addapprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [sp_addrole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [sp_droprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_helprolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
