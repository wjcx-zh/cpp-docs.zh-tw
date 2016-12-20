---
title: "XFORM 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "XFORM"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "XFORM 結構"
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# XFORM 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`XFORM` 結構的形式如下：  
  
## 語法  
  
```  
  
      typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## 備註  
 `XFORM` 結構指定全局空間網頁空間轉換。  **eDx** 和 **eDy** 成員指定水平和垂直轉譯元件，分別。  下表根據作業會顯示如何使用其他成員，例如:  
  
|作業|eM11|eM12|eM21|eM22|  
|--------|----------|----------|----------|----------|  
|`Rotation`|旋轉角度的餘弦函數|旋轉角度的正弦函數|旋轉角度的正弦函數。|旋轉角度的餘弦函數|  
|**縮放**|水平縮放元件|Nothing|Nothing|垂直縮放元件|  
|**剪貼簿**|Nothing|水平縮放常數|垂直的比例常數|Nothing|  
|**反映**|水平反映元件|Nothing|Nothing|垂直反映元件|  
  
## 需求  
 **標頭檔：** wingdi.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../Topic/CRgn::CreateFromData.md)