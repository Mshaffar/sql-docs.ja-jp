---
title: データベースに接続し、既存のオブジェクトを参照する
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.connectionpicker.f1
ms.assetid: 9b331800-3806-4459-ac58-88cdc98124d3
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 65559af8337bc7421f96463a954a212f56a3c269
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75755821"
---
# <a name="how-to-connect-to-a-database-and-browse-existing-objects"></a>操作方法:データベースに接続し、既存のオブジェクトを参照する

データベース管理者と開発者の間で特に共通するタスクとして、ライブ データベースへの接続、データベースのスキーマのデザインまたは参照、データベース オブジェクトの照会などがあります。 Visual Studio の SQL Server オブジェクト エクスプローラーには、専用の **[SQL Server]** ノードが用意されました。このノードの下で、接続されているすべての SQL Server インスタンスとそのデータベースが SSMS のような階層構造でグループ化されます。 接続されている SQL Server インスタンスは、実行中の SQL Server 2008 などのオンプレミス インスタンスであることも、オフプレミスの SQL Azure インスタンスであることも想定されています。  
  
以下の手順では、サンプル データベース AdventureWorks がインストールされていることを前提としています。 別バージョンの SQL Server のサンプル データベースを見つけてインストールするには、[GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を使用してください。 必要に応じ、手順に従って、サーバーにある既存のデータベースを指定することもできます。  
  
### <a name="to-connect-to-a-database-instance"></a>データベース インスタンスに接続するには  
  
1.  Visual Studio で、**SQL Server オブジェクト エクスプローラー**が開いていることを確認します。 開いていない場合は、 **[表示]** メニューの **[SQL Server オブジェクト エクスプローラー]** をクリックします。  
  
2.  **SQL Server オブジェクト エクスプローラー**で **SQL Server** ノードを右クリックし、 **[SQL Server の追加]** をクリックします。  
  
3.  **[サーバーに接続]** ダイアログ ボックスで、接続先のサーバー インスタンスの名前を **[サーバー名]** ボックスに入力し、資格情報を指定して、 **[接続]** をクリックします。  
  
4.  **SQL Server オブジェクト エクスプローラー**で、サーバー インスタンスの下にある **[データベース]** ノードを展開します。 このサーバー インスタンスにあるすべてのデータベースが、この **[データベース]** ノードの下に追加されています。  
  
5.  **AdventureWorks** (または別のデータベース) のノードを展開します。 すべてのデータベース エンティティが、 SQL Server Management Studio に似た階層構造で整理されています。  
  
