---
title: "CFirePropNotifyEvent Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFirePropNotifyEvent"
  - "ATL::CFirePropNotifyEvent"
  - "ATL.CFirePropNotifyEvent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFirePropNotifyEvent class"
  - "連接點 [C++], notifying of events"
  - "sinks, notifying of ATL events"
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CFirePropNotifyEvent Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會通知控制項屬性變更的容器的接收的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CFirePropNotifyEvent  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFirePropNotifyEvent::FireOnChanged](../Topic/CFirePropNotifyEvent::FireOnChanged.md)|\(靜態\) 通知接收控制項容器的屬性已變更。|  
|[CFirePropNotifyEvent::FireOnRequestEdit](../Topic/CFirePropNotifyEvent::FireOnRequestEdit.md)|\(靜態\) 通知接收控制項容器的屬性會變更。|  
  
## 備註  
 `CFirePropNotifyEvent` 會向容器的接收的方法有兩種控制項屬性變更或將變更。  
  
 如果實作控制項的類別 `IPropertyNotifySink`從衍生， `CFirePropNotifyEvent` 叫用方法，當您呼叫 `FireOnRequestEdit` 或 `FireOnChanged`時。  如果您的控制項類別從 `IPropertyNotifySink`並非衍生自類別，此函式會傳回 `S_OK`的呼叫。  
  
 如需建立控制項的詳細資訊，請參閱 [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)