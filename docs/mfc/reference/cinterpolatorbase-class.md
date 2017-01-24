---
title: "CInterpolatorBase 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CInterpolatorBase"
  - "CInterpolatorBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInterpolatorBase 類別"
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInterpolatorBase 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作回呼，當動畫 API 必須計算動畫變數的新值時由此 API 呼叫。  
  
## 語法  
  
```  
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CInterpolatorBase::CInterpolatorBase](../Topic/CInterpolatorBase::CInterpolatorBase.md)|`CInterpolatorBase` 建構物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CInterpolatorBase::CreateInstance](../Topic/CInterpolatorBase::CreateInstance.md)|`CInterpolatorBase` 建立執行個體並將指標傳遞至自訂變更者，處理事件。|  
|[CInterpolatorBase::GetDependencies](../Topic/CInterpolatorBase::GetDependencies.md)|取得插補器的相依性。  \(覆寫 `CUIAnimationInterpolatorBase::GetDependencies`\)。|  
|[CInterpolatorBase::GetDuration](../Topic/CInterpolatorBase::GetDuration.md)|取得插補器的期間。  \(覆寫 `CUIAnimationInterpolatorBase::GetDuration`\)。|  
|[CInterpolatorBase::GetFinalValue](../Topic/CInterpolatorBase::GetFinalValue.md)|取得插補器所導致的最終值。  \(覆寫 `CUIAnimationInterpolatorBase::GetFinalValue`\)。|  
|[CInterpolatorBase::InterpolateValue](../Topic/CInterpolatorBase::InterpolateValue.md)|插補值在指定位移 \(覆寫 `CUIAnimationInterpolatorBase::InterpolateValue`\)。|  
|[CInterpolatorBase::InterpolateVelocity](../Topic/CInterpolatorBase::InterpolateVelocity.md)|插補速度在指定位移 \(覆寫 `CUIAnimationInterpolatorBase::InterpolateVelocity`\)。|  
|[CInterpolatorBase::SetCustomInterpolator](../Topic/CInterpolatorBase::SetCustomInterpolator.md)|儲存將處理事件之自訂插補器的指標。|  
|[CInterpolatorBase::SetDuration](../Topic/CInterpolatorBase::SetDuration.md)|設定變更者的句號 \( `CUIAnimationInterpolatorBase::SetDuration`覆寫\)。|  
|[CInterpolatorBase::SetInitialValueAndVelocity](../Topic/CInterpolatorBase::SetInitialValueAndVelocity.md)|設定插補器的起始值和速度。  \(覆寫 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`\)。|  
  
## 備註  
 這個處理常式建立並傳遞至 `IUIAnimationTransitionFactory::CreateTransition` ，當 `CCustomTransition` 物件建立動畫，在初始化過程的區段 \(開始 `CAnimationController::AnimateGroup`\)。  您通常不需要直接使用此類別，其下摺疊所有事件。 `CCustomInterpolator`衍生類別，指標傳遞給 `CCustomTransition`建構函式。  
  
## 繼承階層架構  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)