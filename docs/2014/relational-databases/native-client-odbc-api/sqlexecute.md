---
title: SQLExecute |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ac50a5abd1f7e87017c6f0c559887b1796032328
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706126"
---
# <a name="sqlexecute"></a>SQLExecute
  ステートメント属性 SQL_SOPT_SS_PARAM_FOCUS が0に設定されていない場合、SQLExecute は SQL_ERROR を返し、SQLSTATE = HY024、メッセージ "無効な属性値、SQL_SOPT_SS_PARAM_FOCUS (実行時にゼロである必要があります)" を含む診断レコードを生成します。 SQL_SOPT_SS_PARAM_FOCUS の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
