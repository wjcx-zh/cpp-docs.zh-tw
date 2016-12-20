---
title: "CCustomInterpolator 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CCustomInterpolator"
  - "CCustomInterpolator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCustomInterpolator 類別"
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCustomInterpolator 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作基本 Interpolator。  
  
## 語法  
  
```  
class CCustomInterpolator;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCustomInterpolator::CCustomInterpolator](../Topic/CCustomInterpolator::CCustomInterpolator.md)|多載。  建構自訂插補器物件，並將期間和速度初始化為指定的值。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCustomInterpolator::GetDependencies](../Topic/CCustomInterpolator::GetDependencies.md)|取得插補器的相依性。|  
|[CCustomInterpolator::GetDuration](../Topic/CCustomInterpolator::GetDuration.md)|取得插補器的期間。|  
|[CCustomInterpolator::GetFinalValue](../Topic/CCustomInterpolator::GetFinalValue.md)|取得插補器所導致的最終值。|  
|[CCustomInterpolator::Init](../Topic/CCustomInterpolator::Init.md)|初始化期間和最終值。|  
|[CCustomInterpolator::InterpolateValue](../Topic/CCustomInterpolator::InterpolateValue.md)|在指定的位移對該值進行插補。|  
|[CCustomInterpolator::InterpolateVelocity](../Topic/CCustomInterpolator::InterpolateVelocity.md)|在指定的位移對速度進行插補|  
|[CCustomInterpolator::SetDuration](../Topic/CCustomInterpolator::SetDuration.md)|設定插補器的期間。|  
|[CCustomInterpolator::SetInitialValueAndVelocity](../Topic/CCustomInterpolator::SetInitialValueAndVelocity.md)|設定插補器的起始值和速度。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CCustomInterpolator::m\_currentValue](../Topic/CCustomInterpolator::m_currentValue.md)|插補後的值。|  
|[CCustomInterpolator::m\_currentVelocity](../Topic/CCustomInterpolator::m_currentVelocity.md)|插補的速度。|  
|[CCustomInterpolator::m\_duration](../Topic/CCustomInterpolator::m_duration.md)|轉換的期間。|  
|[CCustomInterpolator::m\_finalValue](../Topic/CCustomInterpolator::m_finalValue.md)|變數在轉換結束時的最終值。|  
|[CCustomInterpolator::m\_initialValue](../Topic/CCustomInterpolator::m_initialValue.md)|變數在轉換開始時的值。|  
|[CCustomInterpolator::m\_initialVelocity](../Topic/CCustomInterpolator::m_initialVelocity.md)|變數在轉換開始時的速度。|  
  
## 備註  
 從 CCustomInterpolator 衍生類別，並覆寫所有必要的方法以實作自訂的內插補點演算法。  這個類別的指標應該做為參數傳遞至 CCustomTransition。  
  
## 繼承階層架構  
 [CCustomInterpolator](../../mfc/reference/ccustominterpolator-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)