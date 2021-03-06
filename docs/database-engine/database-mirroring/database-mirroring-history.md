---
title: データベース ミラーリングの履歴 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.dbmmonitor.databasemirroringhistory.f1
ms.assetid: 1d6e4b10-4a23-47d7-9918-c417992f09d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 329eda4ba3c0bdabc355242d626a3d0ac89e6033
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "68006426"
---
# <a name="database-mirroring-history"></a>[データベース ミラーリングの履歴]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このダイアログ ボックスは、指定したサーバー インスタンスでミラー化されたデータベースについて、ミラーリング状態の履歴を表示するために使用します。  
  
 **SQL Server Management Studio を使用してデータベース ミラーリングを監視するには**  
  
-   [データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a>オプション  
 **サーバー インスタンス**  
 履歴レポートの対象となるサーバー インスタンスの名前です。  
  
 **[データベース]**  
 履歴レポートの対象となるデータベースの名前です。  
  
 **[一覧のフィルター]**  
 フィルター値が一覧表示されます。 新しい値を選択すると、グリッドが自動的に更新されます。  
  
 使用できるフィルター値は次のとおりです。  
  
-   [過去 2 時間]  
  
-   [過去 4 時間]  
  
-   [過去 8 時間]  
  
-   [過去 1 日間]  
  
-   [過去 2 日間]  
  
-   [最新 100 レコード]  
  
-   [最新 500 レコード]  
  
-   [最新 1000 レコード]  
  
-   [すべてのレコード]  
  
 **[更新]**  
 履歴一覧を更新する場合にクリックします。  
  
> [!NOTE]  
>  このダイアログ ボックスに表示される履歴一覧は、自動的には更新されません。 一覧を更新するには、 **[最新の情報に更新]** をクリックするか、別のフィルター オプションを選択します。 ミラーリング履歴を更新できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。  
  
 **HISTORY**  
 履歴一覧を表示します。 列のヘッダーをクリックすると、その列のデータを使用してグリッドが並べ替えられます。 一覧には次の列があります。  
  
|列名|説明|  
|-----------------|-----------------|  
|**[記録された日時]**|履歴行のタイムスタンプです。|  
|**ロール**|このデータベースに対するサーバー インスタンスの現在のミラーリング ロールです。[プリンシパル] または [ミラー] のいずれかになります。|  
|**[ミラー化の状態]**|データベースの状態。<br /><br /> [Disconnected]\(切断済み\)<br /><br /> [フェールオーバーを保留しています]<br /><br /> Suspended<br /><br /> 同期済み<br /><br /> [同期中]<br /><br /> Unknown|  
|**[ミラーリング監視接続]**|データベースのミラーリング セッションにおけるミラーリング監視接続の状態です。[接続済み] または [接続解除] のいずれかになります。 ミラーリング監視が存在しない場合、値は NULL になります。|  
|**[未送信のログ]**|プリンシパル サーバー インスタンスの送信キューにある未送信ログのサイズをキロバイト (KB) 単位で表します。|  
|**[送信する日時]**|プリンシパル サーバー インスタンスが、送信キューに現在存在するログをミラー サーバー インスタンスに送信するために必要な、おおよその時間です。その際の速度は、 *送信比率*で表されます。 入力トランザクションの送信比率は著しく変化するため、ログの送信にかかる時間は、推定値になります。 ただし、送信比率は、手動フェールオーバーに必要な時間を推定する際の目安として使用できます。|  
|**Send Rate**|トランザクションがミラー サーバー インスタンスに送信される速度 (KB/秒) です。|  
|**[新しいトランザクションの比率]**|入力トランザクションが、プリンシパルのログに記録される速度 (KB/秒) です。 この値と **[送信する日時]** の値を比較することによって、ミラーリングの状況 (遅延している、順調に進行している、遅延が解消されつつあるなど) を確認できます。|  
|**[最も古い未送信のトランザクション]**|送信キュー内で最も古い未送信トランザクションの経過期間。 トランザクションの経過期間は、トランザクションがミラー サーバー インスタンスに送信されないまま経過した時間を分単位で示します。 この値は、データ損失の可能性を時間の観点から測定するのに役立ちます。|  
|**[復元されていないログ]**|再実行キューで待機しているログのサイズ (KB) です。|  
|**[復元する日時]**|現在再実行キューに格納されているログをミラー データベースに適用するために必要な時間の概算値 (分)。|  
|**[復元比率]**|トランザクションがミラー データベースに復元される速度 (KB/秒) です。|  
|**[ミラー コミットのオーバーヘッド]**|トランザクションあたりの平均遅延時間をミリ秒で表します (同期モードのみ)。 この遅延時間は、ミラー サーバー インスタンスによってトランザクションのログ レコードが再実行キューに書き込まれるのをプリンシパル サーバー インスタンスが待機している間、発生したオーバーヘッドの量になります。|  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [データベース ミラーリングの監視 &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
  
