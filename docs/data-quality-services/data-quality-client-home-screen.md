---
title: Data Quality Client のホーム画面
ms.date: 02/29/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.clienthome.f1
ms.assetid: 7c6ec469-bc7d-4d19-8e21-11dcf8ade108
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 8aaf6c9cb9f4c7ed0f006492e6e11ce82ef333f2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "75251726"
---
# <a name="data-quality-client-home-screen"></a>Data Quality Client のホーム画面

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  この画面を使用すると、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) の 3 つの主要なタスク グループ (ナレッジ ベース管理、データ品質プロジェクト、および管理) のそれぞれに対するユーザー インターフェイスにアクセスできます。  
  
## <a name="options"></a>オプション  
  
### <a name="knowledge-base-management"></a>[ナレッジ ベース管理]  
 DQS ナレッジ ベースは、データの品質を向上させるために DQS によって使用されるメタデータのリポジトリです。 このメタデータは、コンピューター支援型のナレッジ検出プロセスの DQS プラットフォームとインタラクティブなドメイン管理プロセスのデータ スチュワードの両者によって作成されます。  
  
 **[新しいナレッジ ベース]**  
 ナレッジ ベースを最初から作成するか、または既存のナレッジ ベースのメタデータに基づいて作成します。 このコマンドによって開くページでは、ナレッジ ベースを識別し、基になる既存のナレッジ ベースを決定し、必要なナレッジ ベース アクティビティを選択して、ナレッジ ベースを作成できます。  
  
 **ナレッジ ベースを開く**  
 ナレッジ ベースを開いて、ナレッジ ベースのドメインを管理し、ナレッジ検出を実行し、照合ポリシーを作成できます。 **[ナレッジ ベースを開く]** ボタンをクリックすると表示される **[ナレッジ ベースを開く]** ページでは、既存のナレッジ ベースの一覧と、それぞれのプロパティ、現在の状態、ナレッジ ベース、ドメインの詳細が示されます。 **[ナレッジ ベースを開く]** でナレッジ ベースを選択して開きます。  
  
 **[最近使用したナレッジ ベース]**  
 画面の一覧から、既に作成されているナレッジ ベースを開きます。 ロックされていない場合は、右矢印をクリックし、ナレッジ ベースを開始するアクティビティを選択します (ドメイン管理、ナレッジ検出、照合ポリシー)。  
  
 ロックされたナレッジ ベースを開いて編集できるのは、自分でロックした場合だけです。 その場合、ナレッジ ベースは閉じたときの状態で開かれます。状態はかっこの中に表示されます。 ナレッジ ベースがロックされていて、自分でロックしたのではない場合は、読み取り専用としてのみ開くことができます。  
  
### <a name="data-quality-projects"></a>データ品質プロジェクト  
 データ品質プロジェクトは、コンピューター支援型のデータ修正とインタラクティブなデータ クレンジングの両方を通じて、DQS がデータ クレンジングとデータ照合を実行するプロセスです。  
  
 **[新しいデータ品質プロジェクト]**  
 新しいプロジェクトを作成するプロジェクトを開始します。 このコマンドによって開くページでは、プロジェクトを識別し、プロジェクトをナレッジ ベースと関連付け、ナレッジ ベースの詳細を表示し、必要なプロジェクト アクティビティを選択して、プロジェクトを作成できます。  
  
 **[データ品質プロジェクトを開く]**  
 プロジェクトを開いて、データ クレンジングまたはデータ照合を実行できます。 **[データ品質プロジェクトを開く]** ボタンをクリックすると表示される **[データ品質プロジェクトを開く]** ページでは、既存のプロジェクトの一覧と、それぞれのプロパティ、現在の状態、ナレッジ ベース、ドメインと照合ポリシー ルールの詳細が示されます。 **[データ品質プロジェクトを開く]** でプロジェクトを選択して開きます。  
  
 **[最近使用したデータ品質プロジェクト]**  
 画面の一覧から、既に作成されているプロジェクトを選択します。 ロックされているプロジェクトは、自分でロックした場合にのみ開くことができます。 その場合、プロジェクトは閉じたときの状態で開かれます。状態はかっこの中に表示されます。 プロジェクトが完了している場合は、アクティビティのエクスポート手順で開かれます。  
  
### <a name="administration"></a>管理  
 DQS 管理では、DQS を監視、構成、および保守することができます。  
  
 **[アクティビティ監視]**  
 接続されている [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]に関連するすべてのアクティビティ (現在のアクティビティと履歴アクティビティの両方) の状態のビューが表示されます。 監視対象となるアクティビティの種類は、ナレッジ マネージメント、データ品質プロジェクト、および SSIS ベースのデータ修正です。  
  
 **構成**  
 参照データサービスアカウントの構成プロパティ (Azure Marketplace を通じて、参照データサービスに直接)、全般設定 (インタラクティブなクレンジング、照合、プロファイル)、およびログの重大度設定を表示します。  
  
## <a name="see-also"></a>参照  
 [DQS のナレッジベースとドメイン](../data-quality-services/dqs-knowledge-bases-and-domains.md)   
 [DQS&#41;&#40;データ品質プロジェクト](../data-quality-services/data-quality-projects-dqs.md)   
 [DQS 管理](../data-quality-services/dqs-administration.md)  
  
  
