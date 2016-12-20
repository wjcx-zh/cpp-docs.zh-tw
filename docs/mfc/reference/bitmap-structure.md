---
title: "BITMAP 結構 | Microsoft Docs"
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
  - "BITMAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BITMAP 結構"
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BITMAP 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**BITMAP** 結構定義高度、寬度、色彩格式，以及邏輯點陣圖的位元值**.**  
  
## 語法  
  
```  
  
      typedef struct tagBITMAP {  /* bm */  
   int bmType;  
   int bmWidth;  
   int bmHeight;  
   int bmWidthBytes;  
   BYTE bmPlanes;  
   BYTE bmBitsPixel;  
   LPVOID bmBits;  
} BITMAP;  
```  
  
#### 參數  
 *bmType*  
 指定點陣圖類型。  在邏輯點陣圖中，成員必須是 0。  
  
 *bmWidth*  
 以像素為單位指定點陣圖的寬度。  寬度必須大於 0。  
  
 *bmHeight*  
 以光柵行為單位指定點陣圖的高度。  高度必須大於 0。  
  
 *bmWidthBytes*  
 在每個光柵行指定位元組數。  這個值必須是偶數，因為繪圖裝置介面 \(Graphics Device \(GDI\) 假設點陣圖格式的位元值為整數\(2 位元組\) 值陣列。  換句話說， **bmWidthBytes** \* 8 在 **bmWidth** 成員乘以 **bmBitsPixel** 成員時，必須是下一個 16 的倍數大於或等於取得的值。  
  
 *bmPlanes*  
 在點陣圖指定色彩平面的數目。  
  
 *bmBitsPixel*  
 在需要定義像素的每個平面上指定相鄰色彩位元的數量。  
  
 *bmBits*  
 指向點陣圖中位元值的位置。  **bmBits** 成員必須為指向 1 位元組值陣列的長指標。  
  
## 備註  
 目前所使用的點陣圖格式為單色和彩色。  單色點陣圖使用 1 位元、 1 平面格式。  每個掃描為 16 的倍數位元組。  
  
 掃描的組織方式如下為高度 *n*的單色點陣圖：  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 在單色裝置的像素不是黑色就是白色。  如果在點陣圖中的對應位元為 1 ，像素已開啟 \(白色\)。  如果在點陣圖中的對應位元為0，像素已關閉 \(黑色\)。  
  
 所有裝置支援為 **RC\_BITBLT** 位元設定在 [CDC::GetDeviceCaps](../Topic/CDC::GetDeviceCaps.md) 成員函式的 **RASTERCAPS** 索引的點陣圖。  
  
 每個裝置有自己獨特的色彩格式。  若要從一個裝置將點陣圖儲存至另一個裝置，請使用 [GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879) 和 [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) Windows 函式。  
  
## 需求  
 **標頭檔：** wingdi.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap::CreateBitmapIndirect](../Topic/CBitmap::CreateBitmapIndirect.md)