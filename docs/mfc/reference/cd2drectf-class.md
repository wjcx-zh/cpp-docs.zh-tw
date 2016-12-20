---
title: "CD2DRectF 類別 | Microsoft Docs"
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
  - "afxrendertarget/CD2DRectF"
  - "CD2DRectF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DRectF 類別"
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DRectF 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`D2D1_RECT_F`的包裝函式。  
  
## 語法  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRectF::CD2DRectF](../Topic/CD2DRectF::CD2DRectF.md)|多載。  從 `D2D1_RECT_F` 物件的 `CD2DRectF` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRectF::IsNull](../Topic/CD2DRectF::IsNull.md)|傳回值的 `boolean` 值運算式不包含有效的資料 \(`null`\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRectF::operator CRect](../Topic/CD2DRectF::operator%20CRect.md)|`CRect` 物件相互轉換。 `CD2DRectF` 。|  
  
## 繼承階層架構  
 `D2D1_RECT_F`  
  
 [CD2DRectF](../../mfc/reference/cd2drectf-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)