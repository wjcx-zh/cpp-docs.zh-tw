---
title: "CAnimationRect 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationRect"
  - "afxanimationcontroller/CAnimationRect"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationRect 類別"
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationRect 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作可以動畫顯示其邊緣的矩形功能。  
  
## 語法  
  
```  
class CAnimationRect : public CAnimationBaseObject;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationRect::CAnimationRect](../Topic/CAnimationRect::CAnimationRect.md)|多載。  建構動畫矩形物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationRect::AddTransition](../Topic/CAnimationRect::AddTransition.md)|加入左、上、右方及下方座標的轉換。|  
|[CAnimationRect::GetBottom](../Topic/CAnimationRect::GetBottom.md)|可讓您存取表示下方座標的 CAnimationVariable。|  
|[CAnimationRect::GetDefaultValue](../Topic/CAnimationRect::GetDefaultValue.md)|傳回矩形界限的預設值。|  
|[CAnimationRect::GetLeft](../Topic/CAnimationRect::GetLeft.md)|可讓您存取表示左邊座標的 CAnimationVariable。|  
|[CAnimationRect::GetRight](../Topic/CAnimationRect::GetRight.md)|可讓您存取表示右邊座標的 CAnimationVariable。|  
|[CAnimationRect::GetTop](../Topic/CAnimationRect::GetTop.md)|可讓您存取表示上方座標的 CAnimationVariable。|  
|[CAnimationRect::GetValue](../Topic/CAnimationRect::GetValue.md)|傳回目前的值。|  
|[CAnimationRect::SetDefaultValue](../Topic/CAnimationRect::SetDefaultValue.md)|設定預設值。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationRect::GetAnimationVariableList](../Topic/CAnimationRect::GetAnimationVariableList.md)|將封裝的動畫變數放入清單中。  \(覆寫 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationRect::operator RECT](../Topic/CAnimationRect::operator%20RECT.md)|將 CAnimationRect 轉換為 RECT。|  
|[CAnimationRect::operator\=](../Topic/CAnimationRect::operator=.md)|指派 rect 給 CAnimationRect。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationRect::m\_bFixedSize](../Topic/CAnimationRect::m_bFixedSize.md)|指定矩形是否為固定大小。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationRect::m\_bottomValue](../Topic/CAnimationRect::m_bottomValue.md)|表示動畫矩形下界限的封裝動畫變數。|  
|[CAnimationRect::m\_leftValue](../Topic/CAnimationRect::m_leftValue.md)|表示動畫矩形左界限的封裝動畫變數。|  
|[CAnimationRect::m\_rightValue](../Topic/CAnimationRect::m_rightValue.md)|表示動畫矩形右界限的封裝動畫變數。|  
|[CAnimationRect::m\_szInitial](../Topic/CAnimationRect::m_szInitial.md)|指定動畫矩形的初始大小。|  
|[CAnimationRect::m\_topValue](../Topic/CAnimationRect::m_topValue.md)|表示動畫矩形上界限的封裝動畫變數。|  
  
## 備註  
 CAnimationRect 類別會封裝四個 CAnimationVariable 物件，而且可以在應用程式中表示矩形。  若要在應用程式中使用這個類別，只需具現化這個類別的物件、使用 CAnimationController::AddAnimationObject 將它加入至動畫控制器，然後針對要套用到左、右、上方及下方座標的每個轉換呼叫 AddTransition。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationRect](../../mfc/reference/canimationrect-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)