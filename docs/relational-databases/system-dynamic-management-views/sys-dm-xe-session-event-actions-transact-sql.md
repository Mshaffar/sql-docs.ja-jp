---
title: dm_xe_session_event_actions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_session_event_actions_TSQL
- sys.dm_xe_session_event_actions_TSQL
- dm_xe_session_event_actions
- sys.dm_xe_session_event_actions
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_xe_session_event_actions dynamic management view
ms.assetid: 0c22a546-683e-4c84-ab97-1e9e95304b03
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9ff9864f3d94909cba5acc20123f00caef6bfa3a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829050"
---
# <a name="sysdm_xe_session_event_actions-transact-sql"></a>sys.dm_xe_session_event_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  イベント セッション アクションに関する情報を返します。 アクションは、イベントが発生したときに実行されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|イベントセッションのメモリアドレス。 NULL 値は許可されません。|  
|action_name|**nvarchar(256)**|アクションの名前。 NULL 値は許可されません。|  
|action_package_guid|**uniqueidentifier**|アクションを含むパッケージの GUID。 NULL 値は許可されません。|  
|event_name|**nvarchar(256)**|アクションが関連付けられているイベントの名前。 NULL 値は許可されません。|  
|event_package_guid|**uniqueidentifier**|イベントを含むパッケージの GUID。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|From|終了|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_xe_session_event_actions.event_session_address|sys.dm_xe_sessions.address|多対一|  
|dm_xe_session_event_actions。 action_name、<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name、<br /><br /> sys.dm_xe_session_events.event_package_guid|多対一|  
|dm_xe_session_event_actions。 event_name、<br /><br /> sys.dm_xe_session_event_actions.event_package_guid|sys.dm_xe_objects.name、<br /><br /> sys.dm_xe_objects.package_guid|多対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

