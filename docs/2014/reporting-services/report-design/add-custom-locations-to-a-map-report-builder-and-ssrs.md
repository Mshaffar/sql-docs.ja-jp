---
title: カスタムの場所のマップへの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ca3bf0e120cfe76aa3b58be1ca6a50991b9fb06
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106644"
---
# <a name="add-custom-locations-to-a-map-report-builder-and-ssrs"></a>カスタムの場所のマップへの追加 (レポート ビルダーおよび SSRS)
  マップをレポートに追加した後、ポイントの場所を独自に追加できます。  
  
 レイヤー上のすべてのポイントの表示プロパティは、レイヤーのポイント プロパティのオプションを設定することで制御できます。 選択した埋め込みポイントの表示プロパティをオーバーライドできます。  
  
> [!NOTE]  
>  埋め込みポイントのレイヤー表示プロパティをオーバーライドした場合、加えた変更を元に戻すことはできません。  
  
 詳細については、「 [ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-point-layer"></a>ポイント レイヤーを追加するには  
  
1.  レポート デザイン画面で、マップをクリックして選択し、マップ ペインを表示します。  
  
2.  ツール バーの **[レイヤーの追加]** をクリックします。  
  
3.  ボックスの一覧から、 **[ポイント レイヤーの追加]** をクリックします。 ポイントが定義されていないポイント レイヤーがマップに追加されます。 既定では、ポイント レイヤーは埋め込みポイントに対応します。  
  
### <a name="to-add-a-custom-point"></a>カスタム ポイントを追加するには  
  
1.  レポート デザイン画面で、マップをクリックして選択し、マップ ペインを表示します。  
  
2.  マップ ペインで、種類が **[埋め込み]** のポイント レイヤーを右クリックし、 **[ポイントの追加]** をクリックします。 カーソルが十字に変化します。  
  
3.  ポイントの追加先として、マップ上の場所をクリックします。 選択したレイヤー上のクリックした場所に、埋め込みポイントが追加されます。  
  
### <a name="to-customize-the-display-for-an-embedded-point"></a>埋め込みポイントの表示をカスタマイズするには  
  
1.  ポイントを右クリックし、 **[ポイントのプロパティ]** をクリックします。 **[マップの埋め込みポイントのプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[このレイヤーのポイント オプションをオーバーライドする]** をクリックします。 左ペインに複数のプロパティ ページが表示されます。  
  
3.  ページをクリックし、このポイントに適用する表示プロパティを設定します。  
  
## <a name="see-also"></a>参照  
 [マップ &#40;レポート ビルダーおよび SSRS&#41;](maps-report-builder-and-ssrs.md)   
 [ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
