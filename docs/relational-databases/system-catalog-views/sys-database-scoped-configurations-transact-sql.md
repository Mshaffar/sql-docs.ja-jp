---
title: database_scoped_configurations (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current||= azure-sqldw-latest
ms.openlocfilehash: a463fea7a70b5e01c26a6ff5e93c1c8c1dab32ea
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78288948"
---
# <a name="sysdatabase_scoped_configurations-transact-sql"></a>database_scoped_configurations (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2016-asdb-addw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

構成ごとに1行の値を格納します。 

|列名|データ型|説明|
|-----------------|---------------|-----------------|
|**configuration_id**|**int**|構成オプションの ID。|
|**name**|**nvarchar(60)**|構成オプションの名前。 使用可能な構成の詳細については、「 [ALTER DATABASE スコープ構成 &#40;transact-sql&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)」を参照してください。|
|**value**|**sqlvariant**|プライマリレプリカのこの構成オプションに設定された値。|
|**value_for_secondary**|**sqlvariant**|セカンダリレプリカのこの構成オプションに設定された値。|
|**is_value_default**|**bit** |値が既定値に設定されているかどうかを指定します。|
|**dw_compatibility_level**|**int**|データベースの互換性レベル (プレビュー)。  既定値 = 0 (自動)|

## <a name="permissions"></a><a name="Permissions"></a> Permissions

ロール **public** のメンバーシップが必要です。

## <a name="remarks"></a>Remarks

**Value_for_secondary**の値として NULL が返された場合、セカンダリがプライマリに設定されていることを意味します。
 
データベース スコープ構成設定はデータベースで継承されます。 つまり、特定のデータベースが復元されたり、アタッチされたりしたとき、既存の構成設定が残ります。

## <a name="see-also"></a>参照

[ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)
