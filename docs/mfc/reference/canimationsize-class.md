---
title: "CAnimationSize 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationSize"
  - "CAnimationSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationSize 類別"
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationSize 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作可以動畫顯示其維度的大小物件功能。  
  
## 語法  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationSize::CAnimationSize](../Topic/CAnimationSize::CAnimationSize.md)|多載。  建構動畫大小物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationSize::AddTransition](../Topic/CAnimationSize::AddTransition.md)|加入寬度和高度的轉換。|  
|[CAnimationSize::GetCX](../Topic/CAnimationSize::GetCX.md)|可讓您存取表示寬度的 CAnimationVariable。|  
|[CAnimationSize::GetCY](../Topic/CAnimationSize::GetCY.md)|可讓您存取表示高度的 CAnimationVariable。|  
|[CAnimationSize::GetDefaultValue](../Topic/CAnimationSize::GetDefaultValue.md)|傳回寬度和高度的預設值。|  
|[CAnimationSize::GetValue](../Topic/CAnimationSize::GetValue.md)|傳回目前的值。|  
|[CAnimationSize::SetDefaultValue](../Topic/CAnimationSize::SetDefaultValue.md)|設定預設值。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationSize::GetAnimationVariableList](../Topic/CAnimationSize::GetAnimationVariableList.md)|將封裝的動畫變數放入清單中。  \(覆寫 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationSize::operator CSize](../Topic/CAnimationSize::operator%20CSize.md)|將 CAnimationSize 轉換為 CSize。|  
|[CAnimationSize::operator\=](../Topic/CAnimationSize::operator=.md)|指派 szSrc 給 CAnimationSize。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationSize::m\_cxValue](../Topic/CAnimationSize::m_cxValue.md)|表示動畫大小之寬度的封裝動畫變數。|  
|[CAnimationSize::m\_cyValue](../Topic/CAnimationSize::m_cyValue.md)|表示動畫大小之高度的封裝動畫變數。|  
  
## 備註  
 CAnimationSize 類別會封裝兩個 CAnimationVariable 物件，而且可以在應用程式中表示大小。  例如，您可以使用這個類別，在螢幕上顯示任何二維物件大小的動畫 \(例如矩形、控制項等等\)。  若要在應用程式中使用這個類別，只需具現化這個類別的物件、使用 CAnimationController::AddAnimationObject 將它加入至動畫控制器，然後針對要套用到寬度和 \(或\) 高度的每個轉換呼叫 AddTransition。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationSize](../../mfc/reference/canimationsize-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)