---
title: 最新バージョンとしてバージョンを指定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f34631e979ded7a329939c23a758ccc0c9aea959
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62773478"
---
# <a name="specify-a-version-as-the-latest-version"></a>特定のバージョンを最新バージョンとして指定する
  ソース管理にファイルをチェックインすると、そのバージョンが最新バージョンになります。つまり、その最新バージョンをチェックアウト (取得) するユーザーは、その最新項目のローカル コピーを受け取ることになります。  
  
 ただし、古いバージョンの項目を最新バージョンとして指定したい状況もあります。 たとえば、ファイルをチェックアウトし、そのファイルを修正してからチェックインした後に、 その修正内容を破棄することにしたとします。 既に項目をチェックインしているので、最初のチェックアウトを元に戻すことはできません。 この場合は、最初にチェックアウトしたバージョンを最新バージョンの項目として指定できます。  
  
 最新バージョンとして指定するには、以下の方法があります。  
  
-   **バージョンをピン留め**します。 ファイルのバージョンにピンを設定しても、そのバージョンよりも新しいバージョンが削除されるわけではありません。 ピンを設定したファイルのピンを解除することもできます。 ピンを解除すると、最後にチェックインしたバージョンのファイルが最新バージョンになります。 ただし、ピンを設定したファイルをチェックアウトすることはできません。  
  
-   **指定されたバージョンにロールバック**しています。 あるバージョンにロールバックすると、そのバージョンよりも新しいバージョンはすべてソース管理から削除されます。 その後、残っている最新バージョンをチェックアウトできます。  
  
### <a name="to-pin-a-version"></a>バージョンにピンを設定するには  
  
1.  で[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]、ソリューションを開きます。  
  
2.  ソリューション エクスプローラーで、最新バージョンとして指定するファイルを選択します。  
  
3.  [**ファイル**] メニューの [**ソース管理**] をポイントし、[**参照] をクリックし**ます。  
  
4.  [ファイル>**の** \<履歴] ダイアログボックスで、最新バージョンとして指定するバージョンを選択し、[**ピン留め**] をクリックします。  
  
     選択したバージョンの横に、それがファイルの最新バージョンであることを示すピンの記号が表示されます。 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に別のバージョンが読み込まれている場合は、ファイルの再読み込みのための画面が表示されます。  
  
### <a name="to-roll-back-to-a-version"></a>特定のバージョンにロールバックするには  
  
1.  で[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]、ソリューションを開きます。  
  
2.  ソリューション エクスプローラーで、最新バージョンとして指定する項目を選択します。  
  
3.  [**ファイル**] メニューの [**ソース管理**] をポイントし、[**履歴**] をクリックします。  
  
4.  [**履歴オプション**] ダイアログボックスで、[ **OK** ] をクリックして、[**ファイルの履歴**] ダイアログボックスを表示します。  
  
5.  [**履歴ファイル**] ボックスで、最新バージョンとして指定するバージョンを選択し、[**ロールバック**] をクリックします。  
  
     選択したバージョンよりも新しいバージョンがすべて削除されることを知らせるメッセージが表示されます。  
  
6.  [**はい**] をクリックして、選択したバージョンにロールバックします。  
  
## <a name="see-also"></a>参照  
 [チェックインの管理](../../2014/database-engine/manage-checkins.md)   
 [ファイルのチェックイン](../../2014/database-engine/check-in-files.md)  
  
  
