---
title: Issue 要素
description: SQL Server では、Issue 要素を使用して、ssbdiagnose ユーティリティによって検出された問題が報告されます。 XML 出力ファイルには、報告される問題ごとに 1 つの Issue 要素が含まれています。
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 0f0d339322dea349f7769ae32d7380f70c922539
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83150578"
---
# <a name="issue-element-ssbdiagnose"></a>Issue 要素 (ssbdiagnose)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**ssbdiagnose** ユーティリティによって検出された問題を報告します。 **ssbdiagnose** の XML 出力ファイルには、報告される問題につき 1 つの Issue 要素が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
|属性|説明|  
|---------------|-----------------|  
|**type**|Issue 要素で報告する問題のカテゴリを次に示します。<br /><br /> **"Diagnosis"** では、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成の分析時に検出された構成の問題を報告します。<br /><br /> **"Problem"** では、 **ssbdiagnose** で分析を完了できない場合の原因となった問題を報告します。 問題を修正して、 **ssbdiagnose**を再実行します。<br /><br /> **"Event"** では、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -RUNTIME **チェックの実行時に検出された** イベントを報告します。 イベントが報告されるのは、 **-SHOWEVENTS** が指定されている場合のみです。|  
|**code**|メッセージのエラー番号を示します。|  
|**server**|問題が検出された [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを示します。 既定のインスタンスに問題があった場合、サーバー属性には、コンピューター名のみが含まれます。 既定のインスタンスに問題があった場合、サーバー属性は "ComputerName\ InstanceName" という形式になります。|  
|**database**|問題が検出されたデータベースの名前を示します。|  
|**object**|問題が検出されたオブジェクトの名前を示します。 問題がインスタンス レベルまたはデータベース レベルの問題である場合、オブジェクト属性はインスタンス名またはデータベース名を繰り返します。|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特徴|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、長さは無制限です。|  
|**Value**|エラー メッセージのテキストを返します。|  
|**個数**|報告されたエラーにつき 1 個。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DiagnosticInformation 要素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**子要素**|なし|  
  
## <a name="example"></a>例  
 この要素は、マスター キーを持たないデータベースの 1102 エラーを報告します。このエラーは、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成の分析時に検出されました。  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a>参照  
 [ssbdiagnose ユーティリティ &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
