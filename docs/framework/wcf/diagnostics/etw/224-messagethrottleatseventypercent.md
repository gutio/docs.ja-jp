---
title: "224 - MessageThrottleAtSeventyPercent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 224 - MessageThrottleAtSeventyPercent
## プロパティ  
  
|||  
|-|-|  
|ID|224|  
|キーワード|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|レベル|Warning \(警告\)|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 `MessageThrottleExceeded` イベントは、主要なサービス スロットルの 1 つを超過したときに生成されます。アクティビティの急増が緩やかになり、スロットルの現在の値が現在の制限の 70% である場合は、このイベントが生成されます。このイベントは、アクティビティが緩やかになったときに一度だけ生成されます。現在の値が 70% の基準付近を上下している \(70、69、70、71、70、69 など\) 場合は、最初に 70% に達したときにイベントが生成されます。このイベントが生成された後にスロットル制限を超えた場合は、`MessageThrottleExceeded` イベントが生成されます。  
  
## メッセージ  
 スロットル '%1' の '%2' の制限は 70%% です。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|Throttle Name|`xs:string`|超過したスロットルの名前。`MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。|  
|Limit|`xs:long`|現在構成されている、スロットルの制限。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、'Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名' と定義されます。例: 'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|