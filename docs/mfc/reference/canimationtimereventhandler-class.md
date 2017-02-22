---
title: "CAnimationTimerEventHandler 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationTimerEventHandler"
  - "CAnimationTimerEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationTimerEventHandler 類別"
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CAnimationTimerEventHandler 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作回呼，當發生計時事件時由動畫 API 呼叫。  
  
## 語法  
  
```  
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationTimerEventHandler::CreateInstance](../Topic/CAnimationTimerEventHandler::CreateInstance.md)|建立 `CAnimationTimerEventHandler` 回呼的執行個體。|  
|[CAnimationTimerEventHandler::OnPostUpdate](../Topic/CAnimationTimerEventHandler::OnPostUpdate.md)|處理動畫更新完成後發生的事件。  \(覆寫 `CUIAnimationTimerEventHandlerBase::OnPostUpdate`\)。|  
|[CAnimationTimerEventHandler::OnPreUpdate](../Topic/CAnimationTimerEventHandler::OnPreUpdate.md)|處理動畫更新開始前發生的事件。  \(覆寫 `CUIAnimationTimerEventHandlerBase::OnPreUpdate`\)。|  
|[CAnimationTimerEventHandler::OnRenderingTooSlow](../Topic/CAnimationTimerEventHandler::OnRenderingTooSlow.md)|處理當動畫轉譯畫面播放速率低於所需最小畫面格速率時發生的事件。  \(覆寫 `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`\)。|  
|[CAnimationTimerEventHandler::SetAnimationController](../Topic/CAnimationTimerEventHandler::SetAnimationController.md)|儲存要路由傳送事件之動畫控制器的指標。|  
  
## 備註  
 當您呼叫 CAnimationController::EnableAnimationTimerEventHandler 時，會建立這個事件處理常式，並將其傳遞至 IUIAnimationTimer::SetTimerEventHandler 方法。  
  
## 繼承階層架構  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationTimerEventHandlerBase`  
  
 `CAnimationTimerEventHandler`  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)