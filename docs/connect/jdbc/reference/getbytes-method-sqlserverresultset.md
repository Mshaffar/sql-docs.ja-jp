---
title: getBytes メソッド (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d16a0aea-6144-4fcb-bcbc-5d7daa36d327
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4ad0ac453e5b048c4db9654a28ab3585a0257c0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921568"
---
# <a name="getbytes-method-sqlserverresultset"></a>getBytes メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列の値が、Java プログラミング言語の **byte** 配列として取得されます。  
  
## <a name="overload-list"></a>オーバーロードの一覧  
  
|Name|説明|  
|----------|-----------------|  
|[getBytes (int)](../../../connect/jdbc/reference/getbytes-method-int-sqlserverresultset.md)|この [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列インデックスの値が、Java プログラミング言語の **byte** 配列として取得されます。|  
|[getBytes (java.lang.String)](../../../connect/jdbc/reference/getbytes-method-java-lang-string-sqlserverresultset.md)|[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列名の値が、Java プログラミング言語の **byte** 配列として取得されます。|  
  
## <a name="remarks"></a>解説  
 以前のバージョンの [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] では、SQLServerResultSet.getBytes を使用してバイト配列と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型の **date**、**time**、**datetime2**、または **datetimeoffset** との間の変換を実行できました。 新しいバージョンでは、これらのデータ型に対してこのメソッドを使用すると、変換がサポートされていないことを示す例外が発生します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
