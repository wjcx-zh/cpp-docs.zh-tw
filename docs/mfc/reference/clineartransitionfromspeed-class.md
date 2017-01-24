---
title: "CLinearTransitionFromSpeed 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CLinearTransitionFromSpeed"
  - "CLinearTransitionFromSpeed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLinearTransitionFromSpeed 類別"
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLinearTransitionFromSpeed 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝線性速度轉換。  
  
## 語法  
  
```  
class CLinearTransitionFromSpeed : public CBaseTransition;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](../Topic/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed.md)|建構線性速度轉換物件，並使用速度與最終值將它初始化。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CLinearTransitionFromSpeed::Create](../Topic/CLinearTransitionFromSpeed::Create.md)|呼叫轉換程式庫，以建立封裝的轉換 COM 物件。  \(覆寫 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)\)。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CLinearTransitionFromSpeed::m\_dblFinalValue](../Topic/CLinearTransitionFromSpeed::m_dblFinalValue.md)|動畫變數在轉換結束時的值。|  
|[CLinearTransitionFromSpeed::m\_dblSpeed](../Topic/CLinearTransitionFromSpeed::m_dblSpeed.md)|變數的速度的絕對值。|  
  
## 備註  
 在線性速度轉換期間，動畫變數的值會按照指定的速率變更。  轉換的期間取決於初始值與指定之最終值間的差值。  因為會自動清除所有的轉換，建議使用 new 運算子來配置它們。  CAnimationController::AnimateGroup 會建立封裝的 IUIAnimationTransition COM 物件，在此之前，這個物件都是 NULL。  在建立這個 COM 物件之後變更成員變數沒有任何作用。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)