---
title: supportsPositionedDelete メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsPositionedDelete
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8011659a-d74b-489b-a88b-08bd9e8b48b2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01781a15d618c0dcb6d68b5716484fc236d9fe75
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920066"
---
# <a name="supportspositioneddelete-method-sqlserverdatabasemetadata"></a>supportsPositionedDelete メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが位置指定された DELETE ステートメントをサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsPositionedDelete()  
```  
  
## <a name="return-value"></a>戻り値  
 サポートされている場合は、**true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsPositionedDelete メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsPositionedDelete メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
