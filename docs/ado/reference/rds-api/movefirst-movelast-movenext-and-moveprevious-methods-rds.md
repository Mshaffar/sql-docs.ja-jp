---
title: MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- MoveLast method [RDS]
- MovePrevious method [RDS]
- MoveFirst method [RDS]
- MoveNext method [RDS]
ms.assetid: 45c80bb5-136f-4204-9df2-78740fa55574
author: rothja
ms.author: jroth
ms.openlocfilehash: 096ad338f1ec9f039a6c63366984aee4d891c202
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82751599"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-rds"></a>MoveFirst、MoveLast、MoveNext、MovePrevious メソッド (RDS)
指定された[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト内の最初、最後、次、または前のレコードに移動します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.Recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 RDS を表すオブジェクト変数です[。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 RDS で**Move**メソッドを使用でき**ます。DataControl**オブジェクトを使用して、Web ページ上のデータバインドコントロール内のデータレコード間を移動します。 たとえば、RDS にバインドすることによって、**レコードセット**をグリッドに表示するとし**ます。DataControl**オブジェクト。 次に、ユーザーがクリックして、表示されている**レコードセット**内の最初、最後、次、または前のレコードに移動するためのボタンを追加できます。 これを行うには、RDS の**MoveFirst**、 **MoveLast**、 **MoveNext**、および**MovePrevious**の各メソッドを呼び出し**ます。** First、Last、Next、および Previous の各ボタンの onClick プロシージャ内の DataControl オブジェクト。 [アドレス帳の例](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)では、これを行う方法を示しています。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [Move メソッド (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveRecord メソッド (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)


