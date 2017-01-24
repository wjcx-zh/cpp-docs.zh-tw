---
title: "CConstantTransition 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CConstantTransition"
  - "CConstantTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CConstantTransition 類別"
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CConstantTransition 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝常數的轉換。  
  
## 語法  
  
```  
class CConstantTransition : public CBaseTransition;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CConstantTransition::CConstantTransition](../Topic/CConstantTransition::CConstantTransition.md)|建構轉換物件，並初始化它的期間。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CConstantTransition::Create](../Topic/CConstantTransition::Create.md)|呼叫轉換程式庫，以建立封裝的轉換 COM 物件。  \(覆寫 [CBaseTransition::Create](../Topic/CBaseTransition::Create.md)\)。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CConstantTransition::m\_duration](../Topic/CConstantTransition::m_duration.md)|轉換的期間。|  
  
## 備註  
 在常數轉換期間，動畫變數的值會在轉換期間維持為初始值。  因為會自動清除所有的轉換，建議使用 new 運算子來配置它們。  CAnimationController::AnimateGroup 會建立封裝的 IUIAnimationTransition COM 物件，在此之前，這個物件都是 NULL。  在建立這個 COM 物件之後變更成員變數沒有任何作用。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CConstantTransition](../../mfc/reference/cconstanttransition-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)