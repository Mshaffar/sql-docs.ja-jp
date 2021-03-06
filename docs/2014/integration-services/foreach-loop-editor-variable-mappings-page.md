---
title: '[Foreach ループエディター] ([変数のマッピング] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03488e4cfd3a0cc905a58166f381f68eb3292c49
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66058532"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>[ForEach ループ エディター] ([変数のマッピング] ページ)
  **[Foreach ループ エディター]** ダイアログ ボックスの **[変数のマッピング]** ページを使用すると、コレクションの値に変数をマップできます。 変数の値は、ループの各反復処理でコレクションの値を使用して更新されます。  
  
 Integration Services パッケージでの Foreach Loop コンテナーの使用方法の詳細については、「 [Foreach Loop Container](control-flow/foreach-loop-container.md) 」を参照してください。 構成方法の詳細については、「 [Foreach ループ コンテナーを構成する](../../2014/integration-services/configure-a-foreach-loop-container.md)」を参照してください。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]簡単な ETL パッケージの作成」チュートリアルには、Foreach ループを追加して構成する方法を示すレッスンが含まれてい[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]ます。  
  
## <a name="options"></a>オプション  
 **変数**  
 既存の変数を選択するか\<、[**新しい変数...**>] をクリックして新しい変数を作成します。  
  
> [!NOTE]  
>   変数をマップした後、新しい行が **[変数]** リストに自動的に追加されます。  
  
 **関連トピック**: [SSIS&#41; 変数の Integration Services &#40;](integration-services-ssis-variables.md)[変数の追加](../../2014/integration-services/add-variable.md)  
  
 **インデックス**  
 Foreach Item 列挙子を使用する場合、変数にマップするコレクションの値に列のインデックスを指定します。 他の列挙子の型では、インデックスは読み取り専用です。  
  
> [!NOTE]  
>  インデックスは 0 から始まります。  
  
 **関連トピック**: [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する方法](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **削除**  
 変数を選択し、 **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Foreach ループエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [Foreach ループエディター &#40;コレクションページ&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [For ループ コンテナー](control-flow/for-loop-container.md)  
  
  
