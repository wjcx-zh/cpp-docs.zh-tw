---
title: "CD2DRectU 類別 | Microsoft Docs"
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
  - "CD2DRectU"
  - "afxrendertarget/CD2DRectU"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DRectU 類別"
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DRectU 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`D2D1_RECT_U`的包裝函式。  
  
## 語法  
  
```  
class CD2DRectU : public D2D1_RECT_U;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRectU::CD2DRectU](../Topic/CD2DRectU::CD2DRectU.md)|多載。  從 `D2D1_RECT_U` 物件的 `CD2DRectU` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRectU::IsNull](../Topic/CD2DRectU::IsNull.md)|傳回值的 `boolean` 值運算式不包含有效的資料 \(`null`\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRectU::operator CRect](../Topic/CD2DRectU::operator%20CRect.md)|`CRect` 物件相互轉換。 `CD2DRectU` 。|  
  
## 繼承階層架構  
 `D2D1_RECT_U`  
  
 [CD2DRectU](../../mfc/reference/cd2drectu-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)