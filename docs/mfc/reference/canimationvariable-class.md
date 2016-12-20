---
title: "CAnimationVariable 類別 | Microsoft Docs"
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
  - "CAnimationVariable"
  - "afxanimationcontroller/CAnimationVariable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationVariable 類別"
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationVariable 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示動畫變數。  
  
## 語法  
  
```  
class CAnimationVariable;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationVariable::CAnimationVariable](../Topic/CAnimationVariable::CAnimationVariable.md)|建構動畫變數物件。|  
|[CAnimationVariable::~CAnimationVariable](../Topic/CAnimationVariable::~CAnimationVariable.md)|解構函式。  當正在終結 CAnimationVariable 物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationVariable::AddTransition](../Topic/CAnimationVariable::AddTransition.md)|加入轉換。|  
|[CAnimationVariable::ApplyTransitions](../Topic/CAnimationVariable::ApplyTransitions.md)|將內部清單中的轉換加入至腳本。|  
|[CAnimationVariable::ClearTransitions](../Topic/CAnimationVariable::ClearTransitions.md)|清除轉換。|  
|[CAnimationVariable::Create](../Topic/CAnimationVariable::Create.md)|建立基礎動畫變數 COM 物件。|  
|[CAnimationVariable::CreateTransitions](../Topic/CAnimationVariable::CreateTransitions.md)|建立要套用至這個動畫變數的所有轉換。|  
|[CAnimationVariable::EnableIntegerValueChangedEvent](../Topic/CAnimationVariable::EnableIntegerValueChangedEvent.md)|啟用或停用 IntegerValueChanged 事件。|  
|[CAnimationVariable::EnableValueChangedEvent](../Topic/CAnimationVariable::EnableValueChangedEvent.md)|啟用或停用 ValueChanged 事件。|  
|[CAnimationVariable::GetDefaultValue](../Topic/CAnimationVariable::GetDefaultValue.md)|傳回預設值。|  
|[CAnimationVariable::GetParentAnimationObject](../Topic/CAnimationVariable::GetParentAnimationObject.md)|傳回父動畫物件。|  
|[CAnimationVariable::GetValue](../Topic/CAnimationVariable::GetValue.md)|多載。  傳回動畫變數的目前值。|  
|[CAnimationVariable::GetVariable](../Topic/CAnimationVariable::GetVariable.md)|傳回 IUIAnimationVariable COM 物件的指標。|  
|[CAnimationVariable::SetDefaultValue](../Topic/CAnimationVariable::SetDefaultValue.md)|設定預設值，並釋放 IUIAnimationVariable COM 物件。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationVariable::SetParentAnimationObject](../Topic/CAnimationVariable::SetParentAnimationObject.md)|設定動畫變數和動畫物件之間的關聯性。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationVariable::m\_bAutodestroyTransitions](../Topic/CAnimationVariable::m_bAutodestroyTransitions.md)|指定是否要刪除相關的轉換物件。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationVariable::m\_dblDefaultValue](../Topic/CAnimationVariable::m_dblDefaultValue.md)|指定預設值，這個值會傳播到 IUIAnimationVariable。|  
|[CAnimationVariable::m\_lstTransitions](../Topic/CAnimationVariable::m_lstTransitions.md)|包含會將此動畫變數顯示為動畫的轉換清單。|  
|[CAnimationVariable::m\_pParentObject](../Topic/CAnimationVariable::m_pParentObject.md)|封裝此動畫變數之動畫物件的指標。|  
|[CAnimationVariable::m\_variable](../Topic/CAnimationVariable::m_variable.md)|儲存 IUIAnimationVariable COM 物件的指標。  如果尚未建立 COM 物件，或建立失敗，則為 NULL。|  
  
## 備註  
 CAnimationVariable 類別會封裝 IUIAnimationVariable COM 物件。  它也會保留要在腳本中套用至動畫變數的轉換清單。  CAnimationVariable 物件會內嵌在動畫物件中，這些物件可以表示應用程式中的動畫值、點、大小、色彩和矩形。  
  
## 繼承階層架構  
 [CAnimationVariable](../../mfc/reference/canimationvariable-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)