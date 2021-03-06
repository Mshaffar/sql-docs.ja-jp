---
title: server_assembly_modules (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_assembly_modules_TSQL
- sys.server_assembly_modules
- server_assembly_modules
- sys.server_assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_assembly_modules catalog view
ms.assetid: af799e38-2d16-49b2-bcf5-6f9199af899e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a814539e3b04135a5d97ad4d4d7b31546c88e62d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832742"
---
# <a name="sysserver_assembly_modules-transact-sql"></a>server_assembly_modules (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  TA 型のサーバーレベルのトリガーのアセンブリモジュールごとに1行の値を格納します。 このビューは、アセンブリ トリガーを、基になる CLR 実装にマップします。 この関係を**server_triggers**に結合できます。 アセンブリを**master**データベースに読み込む必要があります。 組 (object_id) は、リレーションシップのキーです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|これは、このアセンブリモジュールが定義されているオブジェクトへの外部キー参照です。|  
|**assembly_id**|**int**|このモジュールが作成されたアセンブリの ID。 アセンブリは master データベースに読み込む必要があります。|  
|**assembly_class**|**sysname**|モジュールを定義しているアセンブリ内のクラスの名前。|  
|**assembly_method**|**sysname**|このモジュールを定義するクラス内のメソッドの名前。 集計関数 (AF) の場合は NULL です。|  
|**execute_as_principal_id**|**int**|EXECUTE AS サーバー プリンシパルの ID。<br /><br /> 既定では NULL、または EXECUTE AS CALLER の場合は NULL です。<br /><br /> [自己実行として実行する場合は、指定したプリンシパルの ID \<> です。<br /><br /> -2 = EXECUTE AS OWNER。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
