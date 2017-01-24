---
title: "CDiscreteTransition 類別 | Microsoft Docs"
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
  - "CDiscreteTransition"
  - "afxanimationcontroller/CDiscreteTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDiscreteTransition 類別"
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDiscreteTransition 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝離散的轉換。  
  
## 語法  
  
```  
class CDiscreteTransition : public CBaseTransition;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDiscreteTransition::CDiscreteTransition](../Topic/CDiscreteTransition::CDiscreteTransition.md)|建構離散轉換物件，並初始化它的參數。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDiscreteTransition::Create](../Topic/CDiscreteTransition::Create.md)|呼叫轉換程式庫，以建立封裝的轉換 COM 物件。  \(覆寫 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)\)。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDiscreteTransition::m\_dblFinalValue](../Topic/CDiscreteTransition::m_dblFinalValue.md)|動畫變數在轉換結束時的值。|  
|[CDiscreteTransition::m\_delay](../Topic/CDiscreteTransition::m_delay.md)|要據以延遲即時切換至最終值的時間長度。|  
|[CDiscreteTransition::m\_hold](../Topic/CDiscreteTransition::m_hold.md)|要據以將變數保持在其最終值的時間長度。|  
  
## 備註  
 在離散轉換期間，動畫變數會以指定的延遲時間維持初始值，然後瞬間切換到指定的最終值，並維持該值長達指定的保持時間。  因為會自動清除所有的轉換，建議使用 new 運算子來配置它們。  CAnimationController::AnimateGroup 會建立封裝的 IUIAnimationTransition COM 物件，在此之前，這個物件都是 NULL。  在建立這個 COM 物件之後變更成員變數沒有任何作用。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)