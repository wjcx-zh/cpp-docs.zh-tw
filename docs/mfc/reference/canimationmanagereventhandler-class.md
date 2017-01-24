---
title: "CAnimationManagerEventHandler 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationManagerEventHandler"
  - "CAnimationManagerEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationManagerEventHandler 類別"
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationManagerEventHandler 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作回呼，當動畫管理員的狀態變更時由動畫 API 呼叫。  
  
## 語法  
  
```  
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](../Topic/CAnimationManagerEventHandler::CAnimationManagerEventHandler.md)|建構 `CAnimationManagerEventHandler` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationManagerEventHandler::CreateInstance](../Topic/CAnimationManagerEventHandler::CreateInstance.md)|建立 `CAnimationManagerEventHandler` 物件執行個體。|  
|[CAnimationManagerEventHandler::OnManagerStatusChanged](../Topic/CAnimationManagerEventHandler::OnManagerStatusChanged.md)|在動畫管理員狀態有變更時呼叫。  \(覆寫 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`\)。|  
|[CAnimationManagerEventHandler::SetAnimationController](../Topic/CAnimationManagerEventHandler::SetAnimationController.md)|儲存要路由傳送事件之動畫控制器的指標。|  
  
## 備註  
 當您呼叫 CAnimationController::EnableAnimationManagerEvent 時，會建立這個事件處理常式，並將其傳遞至 IUIAnimationManager::SetManagerEventHandler 方法。  
  
## 繼承階層架構  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationManagerEventHandlerBase`  
  
 `CAnimationManagerEventHandler`  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)