---
title: Analysis Services プロジェクトの XML の表示 (SSDT) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f4826be0fd38118e94921f63e02882935132a4d6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072477"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Analysis Services のプロジェクトでの XML の表示 (SSDT)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベースをプロジェクト モードで操作している場合は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって各オブジェクトの XML 定義がプロジェクト フォルダー内に作成されます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]内で各オブジェクトの XML ファイルの内容を見ることができます。 また、XML ファイルを直接編集することもできますが、変更によって XML を [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で読み取れなくなる可能性があるため、ほとんどの状況ではお勧めできません。  
  
> [!NOTE]  
>  オブジェクトごとにファイルが異なるため、プロジェクト全体の xml コードは表示できませんが、各オブジェクトのコードを確認します。 プロジェクト全体のコードを表示する唯一の方法は、プロジェクトをビルドし、 \<プロジェクト名>. asdatabase ファイルに assl コードを表示することです。  
  
### <a name="to-view-the-xml-code-for-an-object"></a>オブジェクトの XML コードを表示するには  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーでオブジェクトを右クリックし、 **[コードの表示]** をクリックします。  
  
     オブジェクトの XML コードが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に表示されます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services プロジェクトのビルド &#40;SSDT&#41;](build-analysis-services-projects-ssdt.md)  
  
  
