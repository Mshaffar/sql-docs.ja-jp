---
title: ブレークポイントの設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0c2c543343bd602be75d600a489edfd84663790b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62911404"
---
# <a name="set-breakpoints"></a>[ブレークポイントの設定]
  **[ブレークポイントの設定]** ダイアログ ボックスを使用すると、ブレークポイントを有効にしてブレークポイントの動作を制御するためのイベントを指定できます。  
  
## <a name="options"></a>オプション  
 **Enabled**  
 選択すると、イベントのブレークポイントが有効になります。  
  
 **Break Condition**  
 ブレークポイントの設定に使用できるイベントの一覧を表示します。  
  
 **ヒットカウントの種類**  
 ブレークポイントがいつ有効になるかを指定します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**いつも**|ブレークポイントにヒットすると、常に実行が中断されます。|  
|**ヒット カウント (等しい)**|ブレークポイントの発生回数がヒット カウントと等しくなると実行が中断されます。|  
|**[ヒット カウント (より大きいまたは等しい)]**|ブレークポイントの発生回数がヒット カウント以上になると実行が中断されます。|  
|**ヒット カウント (倍数)**|ヒット カウントの倍数だけブレークポイントが発生すると実行が中断されます。 たとえば、このオプションを 5 に設定すると、実行は 5 回ごとに中断されます。|  
  
 **[ヒット カウント]**  
 ブレークをトリガーするヒットの回数を指定します。 ブレークポイントが常に有効になっている場合、このオプションは使用できません。  
  
## <a name="see-also"></a>参照  
 [制御フローのデバッグ](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
