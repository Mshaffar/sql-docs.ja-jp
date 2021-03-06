---
title: OLE DB Driver をいつ使用するか
description: OLE DB Driver for SQL Server をいつ使用するかと、それを他のドライバーから区別するデータ アクセスの概念の概要について説明します。
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 4f3ec9e3eee38b5ba6f2c0140a1f6eb316941a02
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "81727956"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server をいつ使用するか
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータにアクセスする際に使用できるテクノロジの 1 つです。  各種データ アクセス テクノロジの詳細については、「[データ アクセス テクノロジのロードマップ](https://go.microsoft.com/fwlink/?LinkID=179186)」を参照してください。  
  
 アプリケーションのデータ アクセス テクノロジとして OLE DB Driver for SQL Server を使用するかどうかを決める場合は、いくつかの要素を検討する必要があります。  
  
 新しいアプリケーションで、Microsoft Visual C# や Visual Basic などのマネージド プログラミング言語を使用しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がある場合は、.NET Framework に含まれている .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用する必要があります。  
  
 COM ベースのアプリケーションを開発しており、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で導入された新機能にアクセスする必要がある場合は、OLE DB Driver for SQL Server を使用する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要がない場合は、引き続き Windows Data Access Components (WDAC) を使用できます。  
  
 既存の OLE DB アプリケーションの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能にアクセスする必要があるかどうかが重要な問題になります。 アプリケーションが既に完成していて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新機能を必要としない場合は、引き続き WDAC を使用できます。 ただし、[xml データ型](../../t-sql/xml/xml-transact-sql.md)などの新機能にアクセスする必要がある場合は、OLE DB Driver for SQL Server を使用する必要があります。  
  
 行のバージョン管理機能を使用した Read Committed トランザクション分離は OLE DB Driver for SQL Server と MDAC の両方でサポートされていますが、スナップショット トランザクション分離は OLE DB Driver for SQL Server のみでサポートされています。 (プログラミング用語では、"行のバージョン管理機能を使用した Read Committed トランザクション分離" は "Read Committed トランザクション" と同義です)。  
  
 OLE DB Driver for SQL Server と MDAC の違いについては、「[MDAC から OLE DB Driver for SQL Server へのアプリケーションの更新](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server](oledb-driver-for-sql-server.md)  
 [OLE DB の使用法に関するトピック](ole-db-how-to/ole-db-how-to-topics.md)  
  
  
