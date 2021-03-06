---
title: 接続文字列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbbb5b4672a8ea393380063887cfd77b3e910238
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299032"
---
# <a name="connection-strings"></a>接続文字列
接続文字列には、接続を確立するために使用する情報が含まれています。 完全な接続文字列には、接続を確立するために必要なすべての情報が含まれています。 接続文字列は、セミコロンで区切られた一連のキーワードと値のペアです。 (接続文字列の完全な構文については、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明を参照してください)。接続文字列は、次の方法で使用されます。  
  
-   **SQLDriverConnect**。ユーザーとの対話によって接続文字列を補完します。  
  
-   **SQLBrowseConnect**。データソースとの間で接続文字列を反復処理します。  
  
 **SQLConnect**は接続文字列を使用しません。**SQLConnect**の使用は、3つのキーワードと値のペアを持つ接続文字列を使用して接続することに似ています (データソース名と、必要に応じてユーザー ID とパスワードを指定します)。
