---
title: "CAnimationValue 類別 | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationValue"
  - "CAnimationValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationValue 類別"
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationValue 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作有一個值的動畫物件功能。  
  
## 語法  
  
```  
class CAnimationValue : public CAnimationBaseObject;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationValue::CAnimationValue](../Topic/CAnimationValue::CAnimationValue.md)|多載。  建構 CAnimationValue 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationValue::AddTransition](../Topic/CAnimationValue::AddTransition.md)|加入要套用至某個值的轉換。|  
|[CAnimationValue::GetValue](../Topic/CAnimationValue::GetValue.md)|多載。  擷取目前的值。|  
|[CAnimationValue::GetVariable](../Topic/CAnimationValue::GetVariable.md)|可讓您存取封裝的動畫變數。|  
|[CAnimationValue::SetDefaultValue](../Topic/CAnimationValue::SetDefaultValue.md)|設定預設值。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationValue::GetAnimationVariableList](../Topic/CAnimationValue::GetAnimationVariableList.md)|將封裝的動畫變數放入清單中。  \(覆寫 [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationValue::operator DOUBLE](../Topic/CAnimationValue::operator%20DOUBLE.md)|提供 CAnimationValue 和 DOUBLE 之間的轉換。|  
|[CAnimationValue::operator INT32](../Topic/CAnimationValue::operator%20INT32.md)|提供 CAnimationValue 和 INT32 之間的轉換。|  
|[CAnimationValue::operator\=](../Topic/CAnimationValue::operator=.md)|多載。  指派 INT32 值給 CAnimationValue。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAnimationValue::m\_value](../Topic/CAnimationValue::m_value.md)|表示動畫值的封裝動畫變數。|  
  
## 備註  
 CAnimationValue 類別會封裝單一 CAnimationVariable 物件，而且可以在應用程式中表示單一動畫值。  例如，您可以將這個類別用於動畫透明度 \(淡出效果\)、角度 \(旋轉物件\)，或用於任何其他需要根據單一動畫值建立動畫的情況。  若要在應用程式中使用這個類別，只需具現化這個類別的物件、使用 CAnimationController::AddAnimationObject 將它加入至動畫控制器，然後針對要套用到動畫值的每個轉換呼叫 AddTransition。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationValue](../../mfc/reference/canimationvalue-class.md)  
  
## 需求  
 **標頭檔：**afxanimationcontroller.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)