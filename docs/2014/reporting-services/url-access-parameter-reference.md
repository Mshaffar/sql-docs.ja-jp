---
title: URL アクセス パラメーター リファレンス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], display options
- URL access [Reporting Services], report display parameters
ms.assetid: 1c3e680a-83ea-4979-8e79-fa2337ae12a3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5607f9105ec7197ebc96afc91f189ac19969be8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098721"
---
# <a name="url-access-parameter-reference"></a>URL Access Parameter Reference
  次のパラメーターを URL の一部として使用すると、レポートのルック アンド フィールを構成できます。 ここでは、最も一般的なパラメーターについて説明します。 パラメーターは大文字と小文字が区別されます。レポート サーバーに出力する場合は *rs:* 、HTML ビューアーに出力する場合は *rc:* をパラメーターの先頭に追加します。 デバイスや表示拡張機能に固有のパラメーターを指定することもできます。 デバイスに固有のパラメーターの詳細については、「 [URL でデバイス情報設定を指定する](specify-device-information-settings-in-a-url.md)」を参照してください。  
  
> [!IMPORTANT]  
>  SharePoint および `_vti_bin` HTTP プロキシ経由で要求をルーティングする [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プロキシ構文を URL に含めることは重要です。 プロキシによって、HTTP 要求にいくつかのコンテキストが追加されます。これは、SharePoint モード レポート サーバーに対してレポートを適切に実行するために必要なコンテキストです。 例については、「 [Access Report Server Items Using URL Access](access-report-server-items-using-url-access.md)」を参照してください。  
>   
>  レポート パラメーターを URL に含める方法および例については、「 [Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md)」を参照してください。  
  
## <a name="html-viewer-commands-rc"></a>HTML ビューアーのコマンド (rc:)  
 次の表では、 *rc:* というプレフィックスが付いた URL アクセスパラメーターについて説明します。 HTML ビューアーを対象として使用されます。  
  
|パラメーター|説明|値|  
|---------------|-----------------|------------|  
|*Toolbar*|ツール バーの表示と非表示を切り替えます。<br /><br /> `false` *rc:Toolbar* = **重要\* rc: ツールバーは、SharePoint サイトでホストされているレポートを対象とするために、ドメイン名の代わりに IP アドレスを使用する URL アクセス文字列に対しては機能しませ\* \* **ん。|このパラメーターの値が `false` の場合、残りのオプションすべてが無視されます。 このパラメーターを省略すると、サポートされている表示形式でツール バーが自動的に表示されます。 このパラメーターの既定値は `true` です。<br /><br /> `true` <br /> `false`|  
|*Parameters*|ツール バーのパラメーター領域の表示と非表示を切り替えます。<br /><br /> `Native`モードの例:<br /><br /> `http://myrshost/reportserver?/Sales&rc:Parameters=Collapsed`<br /><br /> `SharePoint`モードの例:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rc:Parameters=Collapsed`|このパラメーターを `true` に設定すると、ツール バーのパラメーター領域が表示されます。 このパラメーターを `false` に設定すると、パラメーター領域は表示されません。ユーザーが表示することもできません。 このパラメーターの値を `Collapsed` に設定すると、パラメーター領域は表示されませんが、エンド ユーザーが表示と非表示を切り替えることができます。 このパラメーターの既定値は `true` です。 有効な値は次のとおりです。<br /><br /> `true` <br /> `false` <br /> `Collapsed`|  
|*Zoom*|レポート ズーム値を整数のパーセンテージまたは文字列定数として設定します。<br /><br /> `Native`モードの例:<br /><br /> `http://myrshost/reportserver?/Sales&rc:Zoom=Page Width`<br /><br /> `SharePoint`モードの例:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rc:Zoom=Page Width`|標準的な文字列値には `Page Width` と `Whole Page` などがあります。 Internet Explorer 5.0 よりも前のバージョンの Internet Explorer および[!INCLUDE[msCoName](../includes/msconame-md.md)] 以外のすべてのブラウザーでは、このパラメーターが無視されます。 このパラメーターの既定値は `100` です。|  
|*セクション*|表示するレポートのページを設定します。<br /><br /> `Native`レポートのページ2を表示するモードの例:<br /><br /> `http://myrshost/reportserver?/Sales&rc:Section=2`<br /><br /> `SharePoint`レポートのページ2を表示するモードの例:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rc:Section=2`|レポートのページ数よりも大きい値を設定すると、最後のページが表示されます。 `0` よりも小さい値を設定すると、レポートの 1 ページが表示されます。 このパラメーターの既定値は `1` です。|  
|*FindString*|レポート内で特定のテキスト セットを検索します。<br /><br /> `Native`モードの例:<br /><br /> `http://myrshost/reportserver?/Sales&rc:FindString=Mountain-400`<br /><br /> `SharePoint`モードの例:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rc:FindString=Mountain-400`||  
|*StartFind*|検索する最後のセクションを指定します。<br /><br /> `Native`このモードの例では、Product Catalog サンプルレポートで最初に出現する "マウンテン-400" というテキストが検索されます。このレポートは、ページ1から始まり、5ページ目で終わります。<br /><br /> `http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400`|このパラメーターの既定値は、レポートの最終ページです。|  
|*EndFind*|検索に使用する最終ページの番号を設定します。 たとえば、`5` の値は、検索する最後のページがレポートの 5 ページであることを示します。 このパラメーターは、 *StartFind* パラメーターと一緒に使用します。 前の例の*Startfind*の例を参照してください。|既定値は現在のページ番号です。|  
|*FallbackPage*|検索またはドキュメント マップの選択が失敗した場合に表示するページ番号を設定します。|既定値は現在のページ番号です。|  
|*GetImage*|HTML ビューアー ユーザー インターフェイス用の特定のアイコンを取得します。||  
|*アイコン*|特定の表示拡張機能のアイコンを取得します。||  
|*スタイル*|HTML ビューアーに適用するスタイル シートを指定します。||  
|デバイス情報設定|`rc:tag=value` の形式でデバイス情報設定を指定します。この *tag* は、現在使用されている表示拡張機能に固有のデバイス情報設定の名前です (*Format* パラメーターの説明を参照してください)。 たとえば、IMAGE 表示拡張機能の *OutputFormat* デバイス情報設定を使用すると、URL アクセス文字列に `...&rs:Format=IMAGE&rc:OutputFormat=JPEG`パラメーターを指定することで、レポートを JPEG 画像で表示できます。 拡張機能に固有のすべてのデバイス情報設定の詳細については、「[表示拡張機能のデバイス情報設定 (Reporting Services)](device-information-settings-for-rendering-extensions-reporting-services.md)」を参照してください。||  
  
## <a name="report-server-commands-rs"></a>レポート サーバー コマンド (rs:)  
 次の表では、 *rs:* というプレフィックスが付いた URL アクセスパラメーターについて説明します。これは、レポートサーバーのターゲットとして使用されます。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*コマンド*|アイテムの種類に応じて、カタログ アイテムに対して操作を実行します。 既定値は、URL アクセス文字列で参照されるカタログ アイテムの種類で決まります。 有効な値は次のとおりです。<br /><br /> `ListChildren`フォルダー `GetChildren`の内容を表示します。 フォルダー アイテムは、汎用アイテム ナビゲーション ページに表示されます。<br /><br /> `Native`モードの例:<br /><br /> `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`<br /><br /> `SharePoint`モードの例:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`|  
||`Render`指定されたレポートを表示します。<br /><br /> `Native`モードの例:<br /><br /> `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`<br /><br /> `SharePoint`モードの例:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`|  
||`GetSharedDatasetDefinition`共有データセットに関連付けられている XML 定義を表示します。 クエリ、データセット パラメーター、既定値、データセット フィルター、照合順序や大文字と小文字の区別などのデータ オプションを含む共有データセット プロパティは、定義内に保存されます。 この値を使用するには、共有データセットに対する **Read Report Definition** 権限が必要です。<br /><br /> `Native`モードの例:<br /><br /> `http://localhost/reportserver/?/DataSet1&rs:command=GetShareddatasetDefinition`|  
||`GetDataSourceContents`指定された共有データソースのプロパティを XML として表示します。 ブラウザーで XML がサポートされていて、目的のデータ ソースに対して `Read Contents` 権限が与えられている認証ユーザーである場合は、そのデータ ソース定義が表示されます。<br /><br /> `Native`モードの例:<br /><br /> `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`<br /><br /> `SharePoint`モードの例:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`|  
||`GetResourceContents`リソースがブラウザーと互換性がある場合は、リソースをレンダリングし、HTML ページに表示します。 それ以外の場合は、ファイルまたはリソースを開くか、ディスクに保存するように要求されます。<br /><br /> `Native`モードの例:<br /><br /> `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`<br /><br /> `SharePoint`モードの例:<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`|  
||`GetComponentDefinition`パブリッシュ済みレポートアイテムに関連付けられた XML 定義を表示します。 この値を`Read Contents`使用するには、パブリッシュされたレポートアイテムに対する権限が必要です。|  
|*形式*|レポートを表示する形式を指定します。 一般的な値には、`ATOM`、`HTML4.0`、`MHTML`、`IMAGE`、`EXCEL`、`WORD`、`CSV`、`PDF`、`XML` があります。 既定値は `HTML4.0` です。 詳細については、「 [URL アクセスを使用してレポートをエクスポート](export-a-report-using-url-access.md)」を参照してください。<br /><br /> `Native` のレポート サーバーからレポートの PDF コピーを直接取得する例。<br /><br /> `http://myrshost/ReportServer?/myreport&rs:Format=PDF`<br /><br /> モードの`SharePoint`場合などです。<br /><br /> `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF`|  
|*ParameterLanguage*|ブラウザーの言語とは関係なく、URL で渡されるパラメーターの言語を指定します。 既定値は、ブラウザーの言語です。 値は、`en-us` や `de-de.` などのカルチャ値に設定できます。<br /><br /> `Native` モードで、ブラウザーの言語をオーバーライドし、de-DE というカルチャ値を指定する例。<br /><br /> `http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE`|  
|*スナップショット*|レポート履歴スナップショットに基づいたレポートを表示します。 詳細については、「 [URL アクセスを使用してレポート履歴スナップショットを表示する](render-a-report-history-snapshot-using-url-access.md)」を参照してください。<br /><br /> `Native` モードで、日付が 2003-04-07 でタイムスタンプが 13:40:02 のレポート履歴スナップショットを取得する例。<br /><br /> `http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02`|  
|*PersistStreams*|1 つの永続化ストリームでレポートを表示します。 このパラメーターは、表示レポートをチャンク単位で送信するために画像レンダラーによって使用されます。 URL アクセス文字列でこのパラメーターを使用した後、同じ URL アクセス文字列を、 *GetNextStream* パラメーターではなく *PersistStreams* パラメーターと共に使用すると、永続化ストリームの次のチャンクを取得できます。 この URL コマンドは、最終的に永続化ストリームの末尾に到達した時点で 0 バイト ストリームを返します。 既定値は `false` です。|  
|*GetNextStream*|*PersistStreams* パラメーターを使用してアクセスした永続化ストリームの次のデータ チャンクを取得します。 詳細については、 *PersistStreams*の説明を参照してください。 既定値は `false` です。|  
|*SessionID*|クライアント アプリケーションとレポート サーバー間で確立されたアクティブ レポート セッションを指定します。 このパラメーターの値は、セッション ID に設定されます。<br /><br /> セッション ID をクッキーまたは URL の一部として指定できます。 セッション クッキーを使用しないようにレポート サーバーを構成している場合、指定したセッション ID なしの最初の要求はセッション ID 付きでリダイレクトされます。 レポート サーバーのセッションの詳細については、「 [Identifying Execution State](report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)」を参照してください。|  
|*ClearSession*|値が `true` の場合は、レポート セッションからレポートを削除するようにレポート サーバーに指示します。 認証されているユーザーに関連付けられたすべてのレポート インスタンスがレポート セッションから削除されます (レポートインスタンスは、異なるレポートパラメーター値を使用して、同じレポートを複数回実行するように定義されています)。既定値は`false`です。|  
|*ResetSession*|値が `true` の場合は、レポート セッションのすべてのレポート スナップショットとの関連付けを削除することによって、レポート セッションをリセットするようレポート サーバーに指示します。 既定値は `false` です。|  
|*Showhide のトグル*|レポートのセクションの表示と非表示を切り替えます。 切り替えるセクションを表す正の整数を指定します。|  
  
## <a name="report-viewer-web-part-commands-rv"></a>レポート ビューアー Web パーツのコマンド (rv:)  
 次の表では、SharePoint と統合されているレポート ビューアー Web パーツをターゲットとするために使用する、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の予約済みのレポート パラメーター名について説明します。 これらのパラメーター名の先頭には *rv:* が付いています。 レポート ビューアー Web パーツでは、 *rs:ParameterLanguage* パラメーターも受け取ります。  
  
|パラメーター|アクション|  
|---------------|------------|  
|*Toolbar*|レポート ビューアー Web パーツのツール バーの表示を制御します。 既定値は `Full` です。 可能な値は次のとおりです。<br /><br /> `Full`: ツール バーを完全に表示します。<br /><br /> `Navigation`: ツール バーに改ページのみ表示します。<br /><br /> `None`: ツール バーを表示しません。<br /><br /> <br /><br /> `SharePoint` モードで、ツール バーに改ページのみを表示する例。<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:Toolbar=Navigation`|  
|*HeaderArea*|レポート ビューアー Web パーツのヘッダーの表示を制御します。 既定値は `Full` です。 可能な値は次のとおりです。<br /><br /> `Full`: ヘッダーを完全に表示します。<br /><br /> `BreadCrumbsOnly`: ヘッダーに階層リンクのナビゲーションのみを表示して、アプリケーションでの現在位置をユーザーに示します。<br /><br /> `None`: ヘッダーを表示しません。<br /><br /> <br /><br /> `SharePoint` モードで、ヘッダーに階層リンクのナビゲーションのみを表示する例。<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:HeaderArea=BreadCrumbsOnly`|  
|*Docmapの幅*|レポート ビューアー Web パーツのパラメーター領域の表示幅をピクセル単位で制御します。 既定値は、レポート ビューアー Web パーツの既定値と同じです。 値には、負以外の整数値を指定する必要があります。|  
|*AsyncRender*|レポートが非同期に表示されるかどうかを制御します。 既定値は `true` で、レポートが非同期に表示されることを示します。 この値には、`true` または `false` のブール値を指定する必要があります。|  
|*ParamMode*|レポート ビューアー Web パーツのパラメーター プロンプト領域を全体表示で表示する方法を制御します。  既定値は `Full` です。 有効な値は次のとおりです。<br /><br /> `Full`: パラメーター プロンプト領域を表示します。<br /><br /> `Collapsed`: パラメーター プロンプト領域を折りたたみます。<br /><br /> `Hidden`: パラメーター プロンプト領域を非表示にします。<br /><br /> `SharePoint` モードで、パラメーター プロンプト領域を折りたたむ例。<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:ParamMode=Collapsed`|  
|*DocMapMode*|レポート ビューアー Web パーツのドキュメント マップ領域を全体表示で表示する方法を制御します。 既定値は `Full` です。 有効な値は次のとおりです。<br /><br /> `Full`: ドキュメント マップ領域を表示します。<br /><br /> `Collapsed`: ドキュメント マップ領域を折りたたみます。<br /><br /> `Hidden`: ドキュメント マップ領域を非表示にします。|  
|*DockToolBar*|レポート ビューアー Web パーツのツール バーを上部にドッキングするか、下部にドッキングするかを制御します。 有効な値は `Top` と `Bottom` です。 既定値は `Top` です。<br /><br /> <br /><br /> `SharePoint` モードで、下部にツール バーをドッキングする例。<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:DockToolBar=Bottom`|  
|*ToolBarItemsDisplayMode*|表示するツール バー項目を制御します。 これはビットごとの列挙値です。 ツール バー項目を含めるには、項目の値を合計値に加算します。 たとえば、[アクション] メニューが表示されない場合は、rv:ToolBarItemsDisplayMode=63 (または 0x3F) を使用します。これは 1+2+4+8+16+32 を表します。[アクション] メニュー項目のみを表示する場合は、rv:ToolBarItemsDisplayMode=960 (または 0x3C0) を使用します。  既定値は `-1` です。すべてのツール バー項目を表示します。 有効な値は次のとおりです。<br /><br /> 1 (0x1): **[戻る]** ボタン<br /><br /> 2 (0x2): テキスト検索コントロール<br /><br /> 4 (0x4): ページ ナビゲーション コントロール<br /><br /> 8 (0x8): **[更新]** ボタン<br /><br /> 16 (0x10): **[ズーム]** ボックスの一覧<br /><br /> 32 (0x20): **[Atom フィード]** ボタン<br /><br /> 64 (0x40): **[アクション]** の **[印刷]** メニュー オプション<br /><br /> 128 (0x80): **[アクション]** の **[エクスポート]** サブメニュー<br /><br /> 256 (0x100): **[アクション]** の **[レポート ビルダーで開く]** メニュー オプション<br /><br /> 512 (0x200): **[アクション]** の **[サブスクライブ]** メニュー オプション<br /><br /> 1024 (0x400): **[アクション]** の **[新しいデータの警告]** メニュー オプション<br /><br /> たとえば、モードで`SharePoint` 、[**戻る**] ボタン、テキスト検索コントロール、ページナビゲーションコントロール、および [**更新**] ボタンのみを表示します。<br /><br /> `http://myspsite/_vti_bin/reportserver?http://myspsite002%fShared+Documents%2fmyreport.rdl&rv:DocMapMode=Displayed&rv:ToolBarItemsDisplayMode=15`|  
  
## <a name="see-also"></a>参照  
 [URL アクセス (SSRS)](url-access-ssrs.md)  
  
  
