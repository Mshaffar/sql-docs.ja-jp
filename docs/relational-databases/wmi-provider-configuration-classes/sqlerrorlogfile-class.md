---
title: SqlErrorLogFile クラス
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0dd923f17fe0267edf40d07da982d0856ec4ba06
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "73659052"
---
# <a name="sqlerrorlogfile-class"></a>SqlErrorLogFile クラス
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルの情報の表示に関するプロパティを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a>Properties  
 SQLErrorLogFile クラスは、次のプロパティを定義します。  
  
|||  
|-|-|  
|ArchiveNumber|データ型: **uint32**<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> ログ ファイルのアーカイブ番号。|  
|InstanceName|データ型:**文字列**<br /><br /> アクセスの種類: 読み取り専用<br /><br /> 修飾子: キー<br /><br /> <br /><br /> ログ ファイルが存在する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。|  
|LastModified|データ型: **datetime**<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> ログ ファイルの最終変更日。|  
|LogFileSize|データ型: **uint32**<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> ログ ファイルのサイズ (バイト単位)。|  
|名前|データ型:**文字列**<br /><br /> アクセスの種類: 読み取り専用<br /><br /> 修飾子: キー<br /><br /> <br /><br /> ログ ファイルの名前。|  
  
## <a name="remarks"></a>Remarks  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|[DLL]|Sqlmgmprovider.dll|  
|名前空間|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>例  
 次の例では、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にあるすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルに関する情報を取得します。 この例を実行するに\<は、 *Instance_Name*> をインスタンスの名前 (' Instance1 ' など) に置き換えます。  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a>説明  
 WQL ステートメントで*InstanceName*が指定されていない場合、クエリは既定のインスタンスの情報を返します。 たとえば、次の WQL ステートメントは、既定のインスタンス (MSSQLSERVER) からすべてのログ ファイルに関する情報を返します。  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>セキュリティ  
 WMI を使用し[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]てログファイルに接続するには、ローカルコンピューターとリモートコンピューターの両方に対して次のアクセス許可を持っている必要があります。  
  
-   **Root\Microsoft\SqlServer\ComputerManagement10** WMI 名前空間への読み取りアクセス。 既定では、すべてのユーザーがアカウントの有効化権限による読み取りアクセスを持ちます。  
  
    > [!NOTE]  
    >  WMI のアクセス許可を確認する方法については、「[オフラインログファイルの表示](../../relational-databases/logs/view-offline-log-files.md)」の「セキュリティ」セクションを参照してください。  
  
-   エラー ログを格納したフォルダーへの読み取り権限。 既定では、エラーログは次のパスにあります\<*ドライブ>* は、がインストールさ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<れているドライブを表し、 *InstanceName*> は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの名前です)。  
  
     **ドライブ>: Server\MSSQL11 を実行します。 \<** **\<InstanceName> \MSSQL\Log**  
  
 ファイアウォール経由で接続する場合は、リモート ターゲット コンピューターのファイアウォールで WMI 用に例外が設定されていることを確認する必要があります。 詳細については、「 [Windows Vista 以降で WMI にリモート接続する](https://go.microsoft.com/fwlink/?LinkId=178848)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SqlErrorLogEvent クラス](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogevent-class.md)   
 [オフライン ログ ファイルの表示](../../relational-databases/logs/view-offline-log-files.md)  
  
  
