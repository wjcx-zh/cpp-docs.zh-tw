---
title: "COLORADJUSTMENT 結構 | Microsoft Docs"
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
  - "COLORADJUSTMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLORADJUSTMENT 結構"
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COLORADJUSTMENT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當 `StretchBlt` 模式是 **HALFTONE** 時， `COLORADJUSTMENT` 結構定義視窗 **StretchDIBits** 和 `StretchBlt` 函式所使用的色彩調整值。  
  
## 語法  
  
```  
  
      typedef struct  tagCOLORADJUSTMENT {    /* ca */  
    WORD  caSize;  
    WORD  caFlags;  
    WORD  caIlluminantIndex;  
    WORD  caRedGamma;  
    WORD  caGreenGamma;  
    WORD  caBlueGamma;  
    WORD  caReferenceBlack;  
    WORD  caReferenceWhite;  
    SHORT caContrast;  
    SHORT caBrightness;  
    SHORT caColorfulness;  
    SHORT caRedGreenTint;  
} COLORADJUSTMENT;  
```  
  
#### 參數  
 *caSize*  
 指定結構的大小，以位元組為單位。  
  
 *caFlags*  
 指定應如何準備輸出影像。  這個成員可以設定為 **NULL** 或下列值的任何組合：  
  
-   **CA\_NEGATIVE** 指定應顯示原始影像的底片。  
  
-   **CA\_LOG\_FILTER** 指定應套用至輸出色彩的最後密度的對數函式。  表示這個功能的亮度不足，這會將色彩相反。  
  
 *caIlluminantIndex*  
 指定檢視影像物件下方的光源亮度。  這個成員可以設為下列其中一個值：  
  
-   **ILLUMINANT\_EQUAL\_ENERGY**  
  
-   **ILLUMINANT\_A**  
  
-   **ILLUMINANT\_B**  
  
-   **ILLUMINANT\_C**  
  
-   **ILLUMINANT\_D50**  
  
-   **ILLUMINANT\_D55**  
  
-   **ILLUMINANT\_D65**  
  
-   **ILLUMINANT\_D75**  
  
-   **ILLUMINANT\_F2**  
  
-   **ILLUMINANT\_TURNGSTEN**  
  
-   **ILLUMINANT\_DAYLIGHT**  
  
-   **ILLUMINANT\_FLUORESCENT**  
  
-   **ILLUMINANT\_NTSC**  
  
 *caRedGamma*  
 為主要來源色彩的紅色指定第 n 強度 Gamma 修正值。  值必須在 2,500 到 65,000。  10,000 的值表示沒有 Gamma 修正。  
  
 *caGreenGamma*  
 為主要來源色彩的綠色指定第 n 強度 Gamma 修正值。  值必須在 2,500 到 65,000。  10,000 的值表示沒有 Gamma 修正。  
  
 *caBlueGamma*  
 為主要來源色彩的藍色指定第 n 強度 Gamma 修正值。  值必須在 2,500 到 65,000。  10,000 的值表示沒有 Gamma 修正。  
  
 *caReferenceBlack*  
 為來源色彩指定黑色參考。  比這個黑的所有色彩視為黑色。  值必須在 0 到 4,000。  
  
 *caReferenceWhite*  
 為來源色彩指定白色參考。  比這個亮的所有色彩視為白色。  值必須在 6,000 到 10,000。  
  
 *caContrast*  
 指定要套用至來源物件的對比量。  值必須在 \-100 到 100。  值為 0 表示沒有對比調整。  
  
 *caBrightness*  
 指定要套用至來源物件的亮度量。  值必須在 \-100 到 100。  值為 0 表示沒有亮度調整。  
  
 *caColorfulness*  
 指定要套用至來源物件的彩度量。  值必須在 \-100 到 100。  值為 0 表示沒有彩度調整。  
  
 *caRedGreenTint*  
 指定套用至來源物件的紅色、綠色或色彩調整量。  值必須在 \-100 到 100。  正數會調整往紅色，而負數調整往綠色。  0 表示沒有色彩調整。  
  
## 需求  
 **標頭檔：** wingdi.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../Topic/CDC::GetColorAdjustment.md)