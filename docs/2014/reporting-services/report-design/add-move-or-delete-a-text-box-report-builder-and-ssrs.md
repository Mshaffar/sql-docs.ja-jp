---
title: テキスト ボックスの追加、移動、または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f042cf81-d933-4ac7-9287-c074a46bde98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49ba35fb0ecb5ed70fe737a10ce9a700d4e4c816
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106586"
---
# <a name="add-move-or-delete-a-text-box-report-builder-and-ssrs"></a>テキスト ボックスの追加、移動、または削除 (レポート ビルダーおよび SSRS)
  テキスト ボックスはレポート内で最も一般的に使用されるレポート アイテムです。 テキスト ボックスをレポート本文に追加して、タイトル、パラメーターの選択肢、組み込みフィールド、日付などの情報を表示できます。  
  
 テーブルやマトリックスのすべてのセルは、実際にはテキスト ボックスです。 テーブルおよびマトリックスと共にレポートに表示されるほとんどのレポート データは、レポートの各テキスト ボックスの内容を評価するレポート プロセッサの結果です。 したがってセルは、データ領域の外部にあるその他のテキスト ボックスと同じように書式設定できます。  
  
 テキスト ボックスを一覧データ領域に追加するには、テキスト ボックスを追加してから一覧にドラッグする必要があります。  
  
> [!NOTE]  
>  テキスト ボックスをクリックすると、すぐにテキスト ボックスのテキストを編集できる状態になります。 テキストではなくテキスト ボックスそのものを選択するには、<localizedText>Esc</localizedText> キーを押します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-text-box"></a>テキスト ボックスを追加するには  
  
1.  [デザイン] ビューの **[挿入]** タブで、 **[テキスト ボックス]** をクリックします。  
  
2.  デザイン画面で、ボックスをクリックし、テキスト ボックスの目的のサイズにドラッグします。 または、デザイン画面をクリックして、既定のサイズのテキスト ボックスを作成します。  
  
### <a name="to-add-a-text-box-in-a-list"></a>一覧にテキスト ボックスを追加するには  
  
1.  レポート デザイン ビューの **[挿入]** タブで、 **[一覧]** をクリックします。  
  
2.  デザイン画面で、ボックスをクリックし、一覧の目的のサイズにドラッグします。 または、デザイン画面をクリックして、既定のサイズの一覧を作成します。  
  
3.  **[挿入]** タブの **[テキスト ボックス]** をクリックします。  
  
4.  デザイン画面の手順 1. で追加した一覧内で、ボックスをクリックし、テキスト ボックスの目的のサイズにドラッグします。 または、デザイン画面の一覧の内部をクリックして、既定のサイズのテキスト ボックスを作成します。  
  
5.  テキスト ボックスが一覧内で正しく入れ子になっていることを確認するには、テキスト ボックスを選択します。  
  
    > [!NOTE]  
    >  テキスト ボックスの中をクリックして編集モードになった場合は、&lt;localizedText&gt;Esc&lt;/localizedText&gt; キーを押すとテキスト ボックスを選択できます。  
  
6.  プロパティ ペインで、 **Parent** プロパティが一覧データ領域に自動的に追加された四角形であることを確認します。  
  
    > [!NOTE]  
    >  プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** をオンにします。  
  
### <a name="to-move-a-text-box"></a>テキスト ボックスを移動するには  
  
1.  レポート デザイン ビューで、テキスト ボックス内の空白部分をクリックして、テキスト ボックスを選択します。  
  
    > [!NOTE]  
    >  テキスト ボックスの中をクリックして編集モードになった場合は、&lt;localizedText&gt;Esc&lt;/localizedText&gt; キーを押すとテキスト ボックスを選択できます。  
  
2.  テキスト ボックスのハンドルをクリックし、テキスト ボックスを新しい場所にドラッグします。 または、方向キーを使用して、選択したテキスト ボックスを横方向または縦方向に移動できます。 デザイン画面でテキスト ボックスを細かく移動するには、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながら方向キーを使用します。  
  
### <a name="to-delete-a-text-box"></a>テキスト ボックスを削除するには  
  
1.  レポート デザイン ビューで、テキスト ボックス内の空白部分を右クリックして選択し、 **[削除]** をクリックします。 または、テキスト ボックス内の空白部分をクリックして、<localizedText>Del</localizedText> キーを押します。  
  
    > [!NOTE]  
    >  テキスト ボックスの中をクリックして編集モードになった場合は、&lt;localizedText&gt;Esc&lt;/localizedText&gt; キーを押すとテキスト ボックスを選択できます。  
  
## <a name="see-also"></a>参照  
 [テキストボックス &#40;レポートビルダーおよび SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [キーボード ショートカット (レポート ビルダー)](../report-builder/keyboard-shortcuts-report-builder.md)  
  
  
