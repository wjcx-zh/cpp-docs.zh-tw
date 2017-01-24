---
title: "CParabolicTransitionFromAcceleration 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CParabolicTransitionFromAcceleration"
  - "CParabolicTransitionFromAcceleration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CParabolicTransitionFromAcceleration 類別"
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CParabolicTransitionFromAcceleration 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝拋物線加速轉換。  
  
## 語法  
  
```  
class CParabolicTransitionFromAcceleration : public CBaseTransition;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](../Topic/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration.md)|建構拋物線加速轉換，並使用指定的參數將它初始化。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CParabolicTransitionFromAcceleration::Create](../Topic/CParabolicTransitionFromAcceleration::Create.md)|呼叫轉換程式庫，以建立封裝的轉換 COM 物件。  \(覆寫 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)\)。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CParabolicTransitionFromAcceleration::m\_dblAcceleration](../Topic/CParabolicTransitionFromAcceleration::m_dblAcceleration.md)|動畫變數在轉換期間的加速。|  
|[CParabolicTransitionFromAcceleration::m\_dblFinalValue](../Topic/CParabolicTransitionFromAcceleration::m_dblFinalValue.md)|動畫變數在轉換結束時的值。|  
|[CParabolicTransitionFromAcceleration::m\_dblFinalVelocity](../Topic/CParabolicTransitionFromAcceleration::m_dblFinalVelocity.md)|動畫變數在轉換結束時的速度。|  
  
## 備註  
 在拋物線加速轉換期間，動畫變數的值會由初始值變更為最終值，並結束於指定的速度。  您可以指定加速率來控制變數如何快速達到最終值。  因為會自動清除所有的轉換，建議使用 new 運算子來配置它們。  CAnimationController::AnimateGroup 會建立封裝的 IUIAnimationTransition COM 物件，在此之前，這個物件都是 NULL。  在建立這個 COM 物件之後變更成員變數沒有任何作用。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)