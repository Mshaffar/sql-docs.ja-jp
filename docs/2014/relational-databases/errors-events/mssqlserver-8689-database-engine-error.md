---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9f0853d7db0664e75140c0e5478af19c233a2517
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62761710"
---
# <a name="mssqlserver_8689"></a>MSSQLSERVER_8689
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8689|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|USEPLAN_ERR_NO_DB|  
|メッセージ テキスト|USE PLAN ヒントで指定されたデータベース '%.*ls' は存在しません。 既存のデータベースを指定してください。|  
  
## <a name="explanation"></a>説明  
 USE PLAN ヒントで指定したデータベースが存在しません。  
  
## <a name="user-action"></a>ユーザーの操作  
 USE PLAN ヒントで指定したすべてのデータベースが存在することを確認します。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;クエリヒント](/sql/t-sql/queries/hints-transact-sql-query)   
 [プラン ガイド](../performance/plan-guides.md)  
  
  
