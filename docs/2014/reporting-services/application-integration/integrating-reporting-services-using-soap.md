---
title: SOAP を使用した Reporting Services の統合 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b6fffd65b22900d7c505c4b50ec290b95fe9ab4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63126192"
---
# <a name="integrating-reporting-services-using-soap"></a>SOAP を使用した Reporting Services の統合
  SOAP [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API には、カスタムレポートソリューションを開発するための Web サービスエンドポイントがいくつか用意されています。 現在、このエンドポイントは、管理と実行という 2 つのカテゴリに分類されます。 管理機能は、<xref:ReportService2005> エンドポイント、<xref:ReportService2006> エンドポイント、および <xref:ReportService2010> エンドポイントを介して公開されます。 <xref:ReportService2005> エンドポイントは、ネイティブ モードで構成されたレポート サーバーを管理するために使用され、<xref:ReportService2006> エンドポイントは、SharePoint 統合モード用に構成されたレポート サーバーを管理するために使用されます。 <xref:ReportService2010> は、<xref:ReportService2005> と <xref:ReportService2006> の機能をまとめたものであり、ネイティブ モード用または SharePoint 統合モード用に構成されているレポート サーバーを管理できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] では、<xref:ReportService2005> エンドポイントと <xref:ReportService2006> エンドポイントは非推奨です。 <xref:ReportService2010> エンドポイントには、両方のエンドポイントの機能と追加の管理機能が含まれています。  
  
 実行機能は <xref:ReportExecution2005> エンドポイントを介して公開され、レポート サーバーがネイティブ モードまたは SharePoint 統合モードで構成されているときに使用されます。 次の各トピックでは、これらのエンドポイントを使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows、SharePoint、および Web アプリケーションでどのようにレポート ソリューションを開発するかについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows アプリケーションでの SOAP API の使用](integrating-reporting-services-using-soap-windows-application.md)  
 SOAP API を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Windows 環境に統合する方法について説明します。  
  
 [Web アプリケーションでの SOAP API の使用](integrating-reporting-services-using-soap-web-application.md)  
 SOAP API を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Web 環境に統合する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [アプリケーションへの Reporting Services の統合](../application-integration/integrating-reporting-services-into-applications.md)   
 [レポート サーバー Web サービス](../report-server-web-service/report-server-web-service.md)   
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
