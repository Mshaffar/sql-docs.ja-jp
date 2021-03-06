---
title: Synchronize メソッド (RDS) |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Synchronize method [ADO]
ms.assetid: 7af42866-7db2-4174-8251-388a2cf741f2
author: rothja
ms.author: jroth
ms.openlocfilehash: 98254c2f26db08b7c5308248c596b7f70264f10c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750570"
---
# <a name="synchronize-method-rds"></a>Synchronize メソッド (RDS)
指定したレコードセットを、ADO 2.5 以降で使用する接続文字列で指定されたデータベースと同期します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Synchronize(ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray, [lcid As Long], [pInformation)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *文字列*  
 要求が送信される OLE DB プロバイダーに接続するために使用される文字列。 ハンドラーが使用されている場合、ハンドラーは接続文字列を編集または置換できます。  
  
 *HandlerString*  
 文字列は、この実行で使用されるハンドラーを識別します。 文字列には2つの部分が含まれています。 最初の部分には、使用するハンドラーの名前 (ProgID) が含まれています。 文字列の2番目の部分には、ハンドラーに渡される引数が含まれています。 引数文字列の解釈方法は、ハンドラー固有です。 2つの部分は、文字列内のコンマの最初のインスタンスによって区切られます (ただし、引数の文字列には追加のコンマが含まれる場合があります)。 引数は省略可能です。  
  
 *lSynchronizeOptions*  
 同期オプションのビットマスク。  
  
 1 = データベースに対する*Updatetransact*更新は、トランザクションでラップされます。 更新のいずれかが失敗すると、トランザクションは中止されます。  
  
 2 =*Refreshwithupdate*では、*更新*も*refreshconflicts*も設定されていない場合、行の状態が返されます。  
  
 4 = レコードセットを*更新*するには、データベースの現在のデータを使用して更新します。 保留中の更新はデータベースにプッシュされません。 このビットが設定されていない場合、レコードセットは更新されず、保留中の更新はすべてデータベースにプッシュされます。  
  
 8 =*Refreshconflicts*は、保留中の変更があるすべての行を更新できません。 更新に失敗した行は、データベースの現在のデータで更新されます。  
  
 *ppRecordset*  
 同期されるレコードセットへのポインター。  
  
 *pStatusArray*  
 Synchronize の影響を受ける行の状態の安全な配列を返すために使用されるバリアント。 *Refreshwithupdate*、 *Refresh* 、および*refreshconflicts*のいずれの同期オプションも設定されていない場合は設定されません。  
  
 *lcid*  
 *Pinformation*で返されたエラーを構築するために使用される LCID。  
  
 *pInformation*  
 **Execute**によって返された情報エラーへのポインター。 NULL の場合、エラー情報は返されません。  
  
## <a name="remarks"></a>Remarks  
 *ハンドラー文字列*パラメーターは null にすることができます。 この場合の動作は、RDS サーバーがどのように構成されているかによって異なります。 "MSDFMAP. handler" というハンドラー文字列は、Microsoft 提供のハンドラー (Msdfmap .dll) を使用する必要があることを示します。 "" のハンドラー文字列 "は、" "のハンドラー文字列" は、Msdfmap .dll ハンドラーを使用する必要があり、引数 "sample .ini" をハンドラーに渡す必要があることを示します。 次に、msdfmap .dll は、この引数を、サンプルの .ini を使用して接続とクエリ文字列を確認するための方向として解釈します。  
  
## <a name="applies-to"></a>適用対象  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


