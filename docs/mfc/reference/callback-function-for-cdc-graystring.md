---
title: "CDC::GrayString 的回呼函式 | Microsoft Docs"
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
  - "Callback Function for CDC::GrayString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回呼函式, CDC::GrayString 的"
ms.assetid: 5217e183-df48-426b-931b-6245022ca36f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDC::GrayString 的回呼函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

*OutputFunc* 是由應用程式所提供的回呼函式名稱的預留位置。  
  
## 語法  
  
```  
  
      BOOL CALLBACK EXPORT OutputFunc(   
   HDC hDC,   
   LPARAM lpData,   
   int nCount    
);  
```  
  
#### 參數  
 `hDC`  
 識別具有 `nWidth` 和 `nHeight` 和高度指定的點陣圖的記憶體裝置內容至少寬度設為 `GrayString`。  
  
 `lpData`  
 要繪製的字串的點。  
  
 `nCount`  
 指定字元數輸出。  
  
## 傳回值  
 回呼函式的傳回值必須是表示成功的 **TRUE** ;否則為 **FALSE**。  
  
## 備註  
 回呼函式 \(*OutputFunc*\) 必須繪製影像相對座標 \(0,0\) 而不是 \(*x*， *y\)*。  
  
## 需求  
 **標題:** afxwin.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GrayString](../Topic/CDC::GrayString.md)