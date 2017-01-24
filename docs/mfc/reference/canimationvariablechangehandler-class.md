---
title: "CAnimationVariableChangeHandler 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationVariableChangeHandler"
  - "CAnimationVariableChangeHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationVariableChangeHandler 類別"
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationVariableChangeHandler 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作回呼，當動畫變數的值變更時由動畫 API 呼叫。  
  
## 語法  
  
```  
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|建構 `CAnimationVariableChangeHandler` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CAnimationVariableChangeHandler::CreateInstance`|建立 `CAnimationVariableChangeHandler` 物件執行個體。|  
|[CAnimationVariableChangeHandler::OnValueChanged](../Topic/CAnimationVariableChangeHandler::OnValueChanged.md)|在動畫變數的值已變更時呼叫。  \(覆寫 `CUIAnimationVariableChangeHandlerBase::OnValueChanged`\)。|  
|[CAnimationVariableChangeHandler::SetAnimationController](../Topic/CAnimationVariableChangeHandler::SetAnimationController.md)|儲存要路由傳送事件之動畫控制器的指標。|  
  
## 備註  
 這個事件處理常式會建立並將其傳遞至方法， `IUIAnimationVariable::SetVariableChangeHandler` ，當您呼叫 \(啟用動畫物件封裝的所有動畫變數的這個事件\) 的 `CAnimationVariable::EnableValueChangedEvent` 或 `CAnimationBaseObject::EnableValueChangedEvent` 時。  
  
## 繼承階層架構  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)