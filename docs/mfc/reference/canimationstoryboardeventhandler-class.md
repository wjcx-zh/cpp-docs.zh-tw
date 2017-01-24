---
title: "CAnimationStoryboardEventHandler 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationStoryboardEventHandler"
  - "CAnimationStoryboardEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationStoryboardEventHandler 類別"
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationStoryboardEventHandler 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作回呼，當腳本的狀態變更或更新腳本時由動畫 API 呼叫。  
  
## 語法  
  
```  
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](../Topic/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler.md)|建構 `CAnimationStoryboardEventHandler` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationStoryboardEventHandler::CreateInstance](../Topic/CAnimationStoryboardEventHandler::CreateInstance.md)|建立 `CAnimationStoryboardEventHandler` 回呼的執行個體。|  
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](../Topic/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged.md)|處理事件， `OnStoryboardStatusChanged` 時，就會發生這個腳本的狀態變更 \(覆寫 `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`\)。|  
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](../Topic/CAnimationStoryboardEventHandler::OnStoryboardUpdated.md)|處理事件， `OnStoryboardUpdated` 時，就會更新腳本時 \(覆寫 `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`\)。|  
|[CAnimationStoryboardEventHandler::SetAnimationController](../Topic/CAnimationStoryboardEventHandler::SetAnimationController.md)|儲存要路由傳送事件之動畫控制器的指標。|  
  
## 備註  
 `CAnimationController::EnableStoryboardEventHandler`，當您呼叫時，這個事件處理常式會建立物件並將物件傳遞至 `IUIAnimationStoryboard::SetStoryboardEventHandler` 方法。  
  
## 繼承階層架構  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationStoryboardEventHandlerBase`  
  
 `CAnimationStoryboardEventHandler`  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)