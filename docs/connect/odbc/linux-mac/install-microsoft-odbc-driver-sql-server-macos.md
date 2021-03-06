---
title: Microsoft ODBC Driver for SQL Server をインストールする (macOS)
description: macOS クライアントに Microsoft ODBC Driver for SQL Server をインストールして、データベース接続を有効にする方法について説明します。
ms.date: 03/05/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver, installing
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9daa17d8619fa05ac9abf52a768740eb3e223c77
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488520"
---
# <a name="install-the-microsoft-odbc-driver-for-sql-server-macos"></a>Microsoft ODBC Driver for SQL Server をインストールする (macOS)

この記事では、Microsoft ODBC Driver for SQL Server を macOS にインストール方法について説明します。 また、SQL Server 用のオプションのコマンドライン ツール (`bcp` および `sqlcmd`) と、unixODBC 開発ヘッダーについても説明します。

この記事では、Bash シェルから ODBC ドライバーをインストールするためのコマンドについて説明します。 パッケージを直接ダウンロードする場合は、「[ODBC Driver for SQL Server のダウンロード](../download-odbc-driver-for-sql-server.md)」を参照してください。

## <a name="microsoft-odbc-17"></a>Microsoft ODBC 17

macOS に Microsoft ODBC Driver 17 for SQL Server をインストールするには、次のコマンドを実行します。

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=Y brew install msodbcsql17 mssql-tools
```

> [!IMPORTANT]
> 短期間利用可能だった v17 `msodbcsql` パッケージをインストールしている場合は、`msodbcsql17` パッケージのインストール前に削除する必要があります。 これにより、競合が回避されます。 `msodbcsql17` パッケージは `msodbcsql` v13 パッケージと並行してインストールできます。

## <a name="previous-versions"></a>以前のバージョン

以下のセクションでは、以前のバージョンの Microsoft ODBC Driver を macOS にインストールする手順について説明します。

## <a name="odbc-131"></a><a id="13.1"></a> ODBC 13.1

Microsoft ODBC Driver 13.1 for SQL Server を OS X 10.11 (El Capitan) および macOS 10.12 (Sierra) にインストールするには、次のコマンドを使用します。

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql@13.1.9.2 mssql-tools@14.0.6.0
```

## <a name="driver-files"></a>ドライバー ファイル

macOS 上の ODBC ドライバーは、次のコンポーネントで構成されています。

|コンポーネント|説明|  
|---------------|-----------------|  
|libmsodbcsql.17.dylib または libmsodbcsql.13.dylib|ドライバーのすべての機能を含むダイナミック ライブラリ (`dylib`) ファイル。 このファイルは `/usr/local/lib/` にインストールされます。|  
|`msodbcsqlr17.rll` または `msodbcsqlr13.rll`|ドライバー ライブラリに付随するリソース ファイル。 このファイルは、Driver 17 では `[driver .dylib directory]../share/msodbcsql17/resources/en_US/`、Driver 13 では `[driver .dylib directory]../share/msodbcsql/resources/en_US/` にインストールされます。 | 
|msodbcsql.h|ドライバーを使用するために必要な新しい定義がすべて含まれているヘッダー ファイル。<br /><br /> **注:** msodbcsql.h と odbcss.h を同じプログラムで参照することはできません。<br /><br /> msodbcsql.h は、Driver 17 では `/usr/local/include/msodbcsql17/`、Driver 13 では `/usr/local/include/msodbcsql/` にインストールされます。 |
|LICENSE.txt|使用許諾契約書の条項を含むテキスト ファイル。 このファイルは、Driver 17 では `/usr/local/share/doc/msodbcsql17/`、Driver 13 では `/usr/local/share/doc/msodbcsql/` に配置されます。 |
|RELEASE_NOTES|リリース ノートを含むテキスト ファイル。 このファイルは、Driver 17 では `/usr/local/share/doc/msodbcsql17/`、Driver 13 では `/usr/local/share/doc/msodbcsql/` に配置されます。 |

## <a name="resource-file-loading"></a>リソース ファイルの読み込み

ドライバーが機能するには、リソース ファイルを読み込む必要があります。 このファイルは、ドライバーのバージョンに応じて `msodbcsqlr17.rll` または `msodbcsqlr13.rll` という名前になります。 `.rll` ファイルの場所は、上の表に示されているとおり、ドライバー自体の場所 (`so` または `dylib`) に対して相対的です。 バージョン 17.1 の時点で、相対パスからの読み込みが失敗した場合、ドライバーは既定のディレクトリからも `.rll` の読み込みを試みます。 macOS での既定のリソース ファイル パスは `/usr/local/share/msodbcsql17/resources/en_US/` です

## <a name="troubleshooting"></a>トラブルシューティング

ODBC ドライバーを使用して SQL Server に接続できない場合は、[接続の問題のトラブルシューティング](known-issues-in-this-version-of-the-driver.md#connectivity)に関する記事を参照してください。

## <a name="next-steps"></a>次のステップ

ドライバーをインストールした後は、[C++ の ODBC サンプル アプリケーション](../../odbc/cpp-code-example-app-connect-access-sql-db.md)を試すことができます。 ODBC アプリケーションの開発に関する詳細については、「[アプリケーションの開発](../../../odbc/reference/develop-app/developing-applications.md)」を参照してください。

詳細については、ODBC ドライバーの[リリース ノート](release-notes-odbc-sql-server-linux-mac.md)と[システム要件](system-requirements.md)に関するページを参照してください。
