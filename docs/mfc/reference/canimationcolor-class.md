---
title: "CAnimationColor 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationColor"
  - "afxanimationcontroller/CAnimationColor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationColor 類別"
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationColor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作紅色、綠色和藍色元件可以動畫顯示的色彩功能。  
  
## 語法  
  
```  
class CAnimationColor : public CAnimationBaseObject;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationColor::CAnimationColor](../Topic/CAnimationColor::CAnimationColor.md)|多載。  建構動畫色彩物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationColor::AddTransition](../Topic/CAnimationColor::AddTransition.md)|加入紅色、綠色和藍色元件的轉換。|  
|[CAnimationColor::GetB](../Topic/CAnimationColor::GetB.md)|可讓您存取表示藍色元件的 CAnimationVariable。|  
|[CAnimationColor::GetDefaultValue](../Topic/CAnimationColor::GetDefaultValue.md)|傳回色彩元件的預設值。|  
|[CAnimationColor::GetG](../Topic/CAnimationColor::GetG.md)|可讓您存取表示綠色元件的 CAnimationVariable。|  
|[CAnimationColor::GetR](../Topic/CAnimationColor::GetR.md)|可讓您存取表示紅色元件的 CAnimationVariable。|  
|[CAnimationColor::GetValue](../Topic/CAnimationColor::GetValue.md)|傳回目前的值。|  
|[CAnimationColor::SetDefaultValue](../Topic/CAnimationColor::SetDefaultValue.md)|設定預設值。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationColor::GetAnimationVariableList](../Topic/CAnimationColor::GetAnimationVariableList.md)|將封裝的動畫變數放入清單中。  \(覆寫 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationColor::operator COLORREF](../Topic/CAnimationColor::operator%20COLORREF.md)||  
|[CAnimationColor::operator\=](../Topic/CAnimationColor::operator=.md)|指派 color 給 CAnimationColor。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationColor::m\_bValue](../Topic/CAnimationColor::m_bValue.md)|表示動畫色彩藍色元件的封裝動畫變數。|  
|[CAnimationColor::m\_gValue](../Topic/CAnimationColor::m_gValue.md)|表示動畫色彩綠色元件的封裝動畫變數。|  
|[CAnimationColor::m\_rValue](../Topic/CAnimationColor::m_rValue.md)|表示動畫色彩紅色元件的封裝動畫變數。|  
  
## 備註  
 CAnimationColor 類別會封裝三個 CAnimationVariable 物件，而且可以在應用程式中表示色彩。  例如，您可以使用這個類別，在螢幕上顯示任何物件色彩的動畫 \(例如文字色彩、背景色彩等等\)。  若要在應用程式中使用這個類別，只需具現化這個類別的物件、使用 CAnimationController::AddAnimationObject 將它加入至動畫控制器，然後針對要套用到紅色、綠色及藍色元件的每個轉換呼叫 AddTransition。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationColor](../../mfc/reference/canimationcolor-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)