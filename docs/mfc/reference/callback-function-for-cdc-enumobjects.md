---
title: "CDC::EnumObjects 的回呼函式 | Microsoft Docs"
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
  - "Callback Function for CDC::EnumObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回呼函式, CDC::EnumObjects 的"
ms.assetid: 380088b1-88a5-4fb4-bbb5-dd9e8386572b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDC::EnumObjects 的回呼函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

*ObjectFunc* 名稱是由應用程式所提供的函式名稱的預留位置。  
  
## 語法  
  
```  
  
      int CALLBACK EXPORT ObjectFunc(   
   LPSTR lpszLogObject,   
   LPSTR* lpData    
);  
```  
  
#### 參數  
 *lpszLogObject*  
 指向 [LOGPEN](../../mfc/reference/logpen-structure.md) 或 [LOGBRUSH](../../mfc/reference/logbrush-structure.md) 資料結構，其包含有關物件的邏輯屬性的相關資訊。  
  
 `lpData`  
 指向傳遞至 `EnumObjects` 函式的應用程式所提供的資料。  
  
## 傳回值  
 回呼函式會傳回 `int`。  這個傳回的值是使用者定義的。  如果回呼函式傳回 0， `EnumObjects` 會早一些停止列舉。  
  
## 備註  
 實際的名稱必須被輸出。  
  
## 需求  
 **標題:** afxwin.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::EnumObjects](../Topic/CDC::EnumObjects.md)