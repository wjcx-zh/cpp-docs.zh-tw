---
title: "LOGBRUSH 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LOGBRUSH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LOGBRUSH 結構"
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# LOGBRUSH 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`LOGBRUSH` 結構會定義一個實體筆刷的樣式、色彩和樣式。  Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) 和 [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) 函式會使用它。  
  
## 語法  
  
```  
  
      typedef struct tag LOGBRUSH { /* lb */  
   UINT lbStyle;  
   COLORREF lbColor;  
   LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### 參數  
 `lbStyle`  
 指定筆刷型態。  `lbStyle` 成員必須是下列其中一種模式:  
  
-   **BS\_DIBPATTERN** 裝置無關點陣圖 \(DIB\) 規格定義的圖樣筆刷。  如果 `lbStyle` 是 **BS\_DIBPATTERN**， **lbHatch** 成員包含控制代碼給包裝 DIB。  
  
-   **BS\_DIBPATTERNPT** 裝置無關點陣圖 \(DIB\) 規格定義的圖樣筆刷。  如果 `lbStyle` 是 **BS\_DIBPATTERNPT**， **lbHatch** 成員包含指標給包裝 DIB。  
  
-   **BS\_HATCHED** 規劃的筆刷。  
  
-   **BS\_HOLLOW** 凹陷筆刷。  
  
-   **BS\_NULL** 和 **BS\_HOLLOW**相同。  
  
-   **BS\_PATTERN** 記憶體點陣圖定義的圖樣筆刷。  
  
-   **BS\_SOLID** 實心筆刷。  
  
 `lbColor`  
 指定這個筆刷用於繪製的色彩。  如果 `lbStyle` 是 **BS\_HOLLOW** 和 **BS\_PATTERN** 樣式， **lbColor** 被忽略。  如果 `lbStyle` 是 **BS\_DIBPATTERN** 或 **BS\_DIBPATTERNBT**， **lbColor** 低序位文字指定 [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) 結構的 **bmiColors** 成員是否包含明確紅色，綠色，藍色 \(RGB\) 值或索引目前實現的邏輯調色盤。  **lbColor** 成員必須是下列其中一個值:  
  
-   **DIB\_PAL\_COLORS** 色表包含一些 16 位元索引目前實現的邏輯調色盤。  
  
-   **DIB\_RGB\_COLORS** 色表包含常值 RGB 值。  
  
 *lbHatch*  
 指定影線樣式。  這個意義取決於 `lbStyle`定義的筆刷型態。  如果 `lbStyle` 是 **BS\_DIBPATTERN**， **lbHatch** 成員包含控制代碼給包裝 DIB。  如果 `lbStyle` 是 **BS\_DIBPATTERNPT**， **lbHatch** 成員包含指標給包裝 DIB。  如果 `lbStyle` 是 **BS\_HATCHED**， **lbHatch** 成員指定用於線條的方向建立規劃。  它可以是下列其中一個值：  
  
-   向`HS_BDIAGONAL` 上為 45 度，從左至右規劃  
  
-   `HS_CROSS` 水平和垂直交叉陰影。  
  
-   `HS_DIAGCROSS` 45 度交叉陰影。  
  
-   向下`HS_FDIAGONAL` 為 45 度，從左至右規劃  
  
-   `HS_HORIZONTAL` 層級的規劃  
  
-   `HS_VERTICAL` 垂直規劃  
  
 如果 `lbStyle` 是 **BS\_PATTERN**， **lbHatch** 是控制代碼定義樣式的點陣圖。  如果 `lbStyle` 是 **BS\_SOLID** 或 **BS\_HOLLOW**， **lbHatch** 被忽略。  
  
## 備註  
 雖然控制項 **lbColor** 規劃筆刷的前景色彩， [CDC::SetBkMode](../Topic/CDC::SetBkMode.md) 和 [CDC::SetBkColor](../Topic/CDC::SetBkColor.md) 函式控制項的背景色彩。  
  
## 需求  
 **標頭檔：** wingdi.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)