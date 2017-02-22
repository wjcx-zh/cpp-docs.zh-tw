---
title: "CAnimationPoint 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationPoint"
  - "afxanimationcontroller/CAnimationPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationPoint 類別"
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationPoint 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作可以動畫顯示其座標的點功能。  
  
## 語法  
  
```  
class CAnimationPoint : public CAnimationBaseObject;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationPoint::CAnimationPoint](../Topic/CAnimationPoint::CAnimationPoint.md)|多載。  建構 CAnimationPoint 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationPoint::AddTransition](../Topic/CAnimationPoint::AddTransition.md)|加入 X 和 Y 座標的轉換。|  
|[CAnimationPoint::GetDefaultValue](../Topic/CAnimationPoint::GetDefaultValue.md)|傳回 X 和 Y 座標的預設值。|  
|[CAnimationPoint::GetValue](../Topic/CAnimationPoint::GetValue.md)|傳回目前的值。|  
|[CAnimationPoint::GetX](../Topic/CAnimationPoint::GetX.md)|可讓您存取 X 座標的 CAnimationVariable。|  
|[CAnimationPoint::GetY](../Topic/CAnimationPoint::GetY.md)|可讓您存取 Y 座標的 CAnimationVariable。|  
|[CAnimationPoint::SetDefaultValue](../Topic/CAnimationPoint::SetDefaultValue.md)|設定預設值。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationPoint::GetAnimationVariableList](../Topic/CAnimationPoint::GetAnimationVariableList.md)|將封裝的動畫變數放入清單中。  \(覆寫 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationPoint::operator CPoint](../Topic/CAnimationPoint::operator%20CPoint.md)|將 CAnimationPoint 轉換為 CPoint。|  
|[CAnimationPoint::operator\=](../Topic/CAnimationPoint::operator=.md)|指派 ptSrc 給 CAnimationPoint。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationPoint::m\_xValue](../Topic/CAnimationPoint::m_xValue.md)|表示動畫點 X 座標的封裝動畫變數。|  
|[CAnimationPoint::m\_yValue](../Topic/CAnimationPoint::m_yValue.md)|表示動畫點 Y 座標的封裝動畫變數。|  
  
## 備註  
 CAnimationPoint 類別會封裝兩個 CAnimationVariable 物件，而且可以在應用程式中表示一個點。  例如，您可以使用這個類別，在螢幕上任何物件的位置顯示動畫 \(例如文字字串、圓形、點等等\)。  若要在應用程式中使用這個類別，只需具現化這個類別的物件、使用 CAnimationController::AddAnimationObject 將它加入至動畫控制器，然後針對要套用到 X 和 \(或\) Y 座標的每個轉換呼叫 AddTransition。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationPoint](../../mfc/reference/canimationpoint-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)