---
title: "CD2DSizeF 類別 | Microsoft Docs"
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
  - "afxrendertarget/CD2DSizeF"
  - "CD2DSizeF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DSizeF 類別"
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DSizeF 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

D2D1\_SIZE\_F 的包裝函式。  
  
## 語法  
  
```  
class CD2DSizeF : public D2D1_SIZE_F;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DSizeF::CD2DSizeF](../Topic/CD2DSizeF::CD2DSizeF.md)|多載。  從 `D2D1_SIZE_F` 物件的 `CD2DSizeF` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DSizeF::IsNull](../Topic/CD2DSizeF::IsNull.md)|傳回值的 `boolean` 值運算式不包含有效的資料 \(`null`\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DSizeF::operator CSize](../Topic/CD2DSizeF::operator%20CSize.md)|`CSize` 物件相互轉換。 `CD2DSizeF` 。|  
  
## 繼承階層架構  
 `D2D1_SIZE_F`  
  
 [CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)