---
title: "CSinusoidalTransitionFromRange 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CSinusoidalTransitionFromRange"
  - "CSinusoidalTransitionFromRange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSinusoidalTransitionFromRange 類別"
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSinusoidalTransitionFromRange 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝已指定振動範圍的正弦曲線範圍轉換。  
  
## 語法  
  
```  
class CSinusoidalTransitionFromRange : public CBaseTransition;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](../Topic/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange.md)|建構新的轉換物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSinusoidalTransitionFromRange::Create](../Topic/CSinusoidalTransitionFromRange::Create.md)|呼叫轉換程式庫，以建立封裝的轉換 COM 物件。  \(覆寫 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)\)。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CSinusoidalTransitionFromRange::m\_dblMaximumValue](../Topic/CSinusoidalTransitionFromRange::m_dblMaximumValue.md)|動畫變數的正弦波峰值。|  
|[CSinusoidalTransitionFromRange::m\_dblMinimumValue](../Topic/CSinusoidalTransitionFromRange::m_dblMinimumValue.md)|動畫變數的正弦波谷值。|  
|[CSinusoidalTransitionFromRange::m\_duration](../Topic/CSinusoidalTransitionFromRange::m_duration.md)|轉換的期間。|  
|[CSinusoidalTransitionFromRange::m\_period](../Topic/CSinusoidalTransitionFromRange::m_period.md)|正弦波的振盪週期 \(以秒為單位\)。|  
|[CSinusoidalTransitionFromRange::m\_slope](../Topic/CSinusoidalTransitionFromRange::m_slope.md)|轉換開始處的斜率。|  
  
## 備註  
 動畫變數的值會在正弦範圍轉換的整個期間波動於指定的最小值和最大值之間。  斜率參數會用來明確區分其他參數所指定的兩個可能正弦波。  因為會自動清除所有的轉換，建議使用 new 運算子來配置它們。  CAnimationController::AnimateGroup 會建立封裝的 IUIAnimationTransition COM 物件，在此之前，這個物件都是 NULL。  在建立這個 COM 物件之後變更成員變數沒有任何作用。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)