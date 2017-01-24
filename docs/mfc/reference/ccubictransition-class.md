---
title: "CCubicTransition 類別 | Microsoft Docs"
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
  - "CCubicTransition"
  - "afxanimationcontroller/CCubicTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCubicTransition 類別"
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCubicTransition 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝立方轉換。  
  
## 語法  
  
```  
class CCubicTransition : public CBaseTransition;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCubicTransition::CCubicTransition](../Topic/CCubicTransition::CCubicTransition.md)|建構轉換物件，並初始化它的參數。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCubicTransition::Create](../Topic/CCubicTransition::Create.md)|呼叫轉換程式庫，以建立封裝的轉換 COM 物件。  \(覆寫 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)\)。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CCubicTransition::m\_dblFinalValue](../Topic/CCubicTransition::m_dblFinalValue.md)|動畫變數在轉換結束時的值。|  
|[CCubicTransition::m\_dblFinalVelocity](../Topic/CCubicTransition::m_dblFinalVelocity.md)|變數在轉換結束時的速度。|  
|[CCubicTransition::m\_duration](../Topic/CCubicTransition::m_duration.md)|轉換的期間。|  
  
## 備註  
 在三次方轉換期間，動畫變數的值會在轉換期間由初始值變更為指定的最終值，並結束於指定的速度。  因為會自動清除所有的轉換，建議使用 new 運算子來配置它們。  CAnimationController::AnimateGroup 會建立封裝的 IUIAnimationTransition COM 物件，在此之前，這個物件都是 NULL。  在建立這個 COM 物件之後變更成員變數沒有任何作用。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CCubicTransition](../../mfc/reference/ccubictransition-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)