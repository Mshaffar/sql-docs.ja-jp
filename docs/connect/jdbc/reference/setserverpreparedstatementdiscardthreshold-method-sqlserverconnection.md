---
title: setServerPreparedStatementDiscardThreshold メソッド (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a29b2d8124f0714a6201d88fbdd0a61d580a5429
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927616"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>setServerPreparedStatementDiscardThreshold メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 特定の接続インスタンスの動作を指定します。 この設定では、サーバー上の未処理のハンドルをクリーンアップする呼び出しが実行される前に 1 回の接続あたりに未処理にできる、未処理の準備されたステートメントの破棄アクション (sp_unprepare) の数を制御できます。 設定が 1 以下の場合、準備解除アクションは、準備されたステートメントの終了時に直ちに実行されます。 1 より大きい値に設定した場合、これらの呼び出しは、sp_unprepare を頻繁に呼び出すことによるオーバーヘッドを回避するためにまとめてバッチ処理されます。


## <a name="syntax"></a>構文  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>パラメーター  
 *thresholdValue*  
 
 **serverPreparedStatementDiscardThreshold** 接続プロパティの新しい値です。  
 
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバー バージョン 6.4 以降で使用できます。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
