---
title: fn_virtualservernodes (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_virtualservernodes
- fn_virtualservernodes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- nodes [Faillover Clustering], virtual servers
- nodes [Faillover Clustering]
- virtual servers [Faillover Clustering]
- failover clustering [SQL Server], nodes
- fn_virtualservernodes function
- sys.fn_virtualservernodes function
ms.assetid: 257f3b8d-93c0-4444-87f1-ea211bd8cad0
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da218e1afeec389d69b1727160a420c889225783
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "68059189"
---
# <a name="sysfn_virtualservernodes-transact-sql"></a>fn_virtualservernodes (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを実行できるフェールオーバークラスターインスタンスノードの一覧を返します。 この情報は、フェールオーバー クラスタリング環境で役立ちます。  
  
> [!IMPORTANT]
>  この[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]システム関数は、旧バージョンとの互換性のために用意されています。 代わりに、 [dm_os_cluster_nodes &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)を使用することをお勧めします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_virtualservernodes()  
```  
  
## <a name="tables-returned"></a>返されるテーブル  
 現在の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーがクラスター化されたサーバーの場合、 **fn_virtualservernodes**は、このインスタンスが定義されているフェールオーバークラスターインスタンスノードの一覧を返します。  
  
 現在のサーバーインスタンスがクラスター化されたサーバーでない場合、 **fn_virtualservernodes**は空の行セットを返します。  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーは、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対する VIEW SERVER STATE 権限を持っている必要があります。  
  
## <a name="examples"></a>使用例  
 次の例で`fn_virtualservernodes`は、を使用して、クラスター化されたサーバーインスタンスに対してクエリを実行します。  
  
```  
SELECT * FROM fn_virtualservernodes();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 NodeName  
  
 -------\-  
  
 SS3-CLUSN1  
  
 SS3-CLUSN2  
  
## <a name="see-also"></a>参照  
 [dm_os_cluster_nodes &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [fn_servershareddrives &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)  
  
  
