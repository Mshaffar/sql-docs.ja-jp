---
title: Context プロパティ (SecurityCertificate)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Context Property (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Context property
ms.assetid: 65dd737f-81ce-479e-8219-7b1b4d8f57c7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b471dd43b2f787824cafe789ff8737a00d98e8da
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "73660158"
---
# <a name="context-property-securitycertificate-class"></a>Context プロパティ (SecurityCertificate クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  セキュリティ証明書のコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Context [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 セキュリティ証明書を表す [SecurityCertificate クラス](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 セキュリティ証明書のコンテキストを指定する**sint32**配列値。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
