---
title: "LOGPEN 結構 | Microsoft Docs"
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
  - "LOGPEN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LOGPEN 結構"
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LOGPEN 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

 `LOGPEN` 結構會定義樣式、 寬度和色彩的畫筆、 繪圖物件用來繪製線條和框線。  [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#cpen__createpenindirect) 函式使用 `LOGPEN` 結構。  
  
## <a name="syntax"></a>語法  
  
```  
 
    typedef struct tagLOGPEN {  /* lgpn */  
    UINT lopnStyle;  
    POINT lopnWidth;  
    COLORREF lopnColor;  
} LOGPEN;  
```  
  
#### <a name="parameters"></a>參數  
 *lopnStyle*  
 指定畫筆型別。 這個成員可以是下列值之一︰  
  
- **PS_SOLID** 建立穩固的畫筆。  
  
- **PS_DASH** 建立虛線的畫筆。 （時才有效畫筆寬度為 1。）  
  
- **PS_DOT** 建立十進位的畫筆。 （時才有效畫筆寬度為 1。）  
  
- **PS_DASHDOT** 建立畫筆交替的虛線和點。 （時才有效畫筆寬度為 1。）  
  
- **PS_DASHDOTDOT** 交替的虛線和雙點建立畫筆。 （時才有效畫筆寬度為 1。）  
  
- **PS_NULL** 建立 null 畫筆。  
  
- **PS_INSIDEFRAME** 建立畫筆繪製線條封閉的形狀，所產生的 GDI 輸出函式所指定的周框內 (例如， **橢圓形**, ，**矩形**, ，`RoundRect`, ，`Pie`, ，和 `Chord` 成員函式)。 使用 GDI 使用這個樣式時輸出未指定的周框矩形的函式 (例如， `LineTo` 成員函式)，畫筆的繪圖區域不受限於的外框。  
  
     如果畫筆有 **PS_INSIDEFRAME** 樣式和色彩的不相符的邏輯色彩表，以遞色色彩繪製畫筆。  **PS_SOLID** 畫筆樣式無法用來建立與遞色畫筆。  **PS_INSIDEFRAME** 樣式等同於 **PS_SOLID** 畫筆寬度是否小於或等於 1。  
  
     當 **PS_INSIDEFRAME** 樣式搭配以外的其他函式所產生的 GDI 物件 **橢圓形**, ，**矩形**, ，和 `RoundRect`, ，線條可能不完全在指定的範圍內。  
  
 *lopnWidth*  
 指定畫筆寬度，以邏輯單位表示。 如果 **lopnWidth** 成員為 0，畫筆是 1 個像素寬，不論目前的對應模式點陣裝置上。  
  
 *lopnColor*  
 指定的畫筆色彩。  
  
## <a name="remarks"></a>備註  
  **y** 值 [點](../../mfc/reference/point-structure1.md) 結構 **lopnWidth** 成員不是。  
  
## <a name="requirements"></a>需求  
 **標頭︰** wingdi.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#cpen__createpenindirect)

