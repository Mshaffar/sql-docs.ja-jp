---
title: sp_rda_set_rpo_duration (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3588f12006de3f7a9e79f6743ae8dffbe01f42c2
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82807873"
---
# <a name="syssp_rda_set_rpo_duration-transact-sql"></a>sp_rda_set_rpo_duration (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  特定の時点への復元が必要な場合に、リモートの Azure データベースの完全な復元を確実に行うために、ステージングテーブルに保持 SQL Server れる移行データの時間数を設定します。    
    
 詳細については、「Stretch Database」を参照してください。移行され[た行を一時的に保持することで、Azure データのデータ損失のリスクが軽減](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)されます。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>構文    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>引数    
 [ @duration_hrs =] *duration_hrs*    
 現在の Stretch が有効なデータベースについて SQL Server 保持する移行データの時間数 (null 以外の整数値) を指定します。 既定値と最小値は8時間です。    
 
 > [!NOTE]
 > 値が大きいほど、SQL Server により多くの記憶領域が必要になります。
    
## <a name="permissions"></a>アクセス許可    
 Db_owner のアクセス許可が必要です。    
    
## <a name="remarks"></a>Remarks    
 [Transact-sql&#41;&#40;sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)を実行して現在の値を取得します。    
    
## <a name="see-also"></a>参照    
 [sp_rda_get_rpo_duration &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [Stretch 対応データベースの復元 (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
