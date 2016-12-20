---
title: "CDC::SetAbortProc 的回呼函式 | Microsoft Docs"
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
  - "Callback Function for CDC::SetAbortProc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回呼函式, CDC::SetAbortProc 的"
ms.assetid: daa36d5d-15de-40fc-8d37-a865d06c4710
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDC::SetAbortProc 的回呼函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

名稱 *AbortFunc* 是由應用程式所提供的函式名稱的預留位置。  
  
## 語法  
  
```  
  
      BOOL CALLBACK EXPORT AbortFunc(   
   HDC hPr,   
   int code    
);  
```  
  
#### 參數  
 *hPr*  
 識別裝置內容。  
  
 `code`  
 指定是否發生錯誤。  如果未發生任何錯誤，則為 0。  它是 **SP\_OUTOFDISK** ，如果列印管理員目前的磁碟空間不足，以及更多磁碟空間將變成可用，則應用程式會等待。  如果 `code` 是 **SP\_OUTOFDISK**，應用程式就必須中止列印工作。  如果沒有，它必須產生用於列印管理員呼叫 **PeekMessage** 和 **GetMessage** Windows 函式。  
  
## 傳回值  
 停止處理函式的傳回值為非零，如果列印工作是繼續和 0，則會被移除。  
  
## 備註  
 必須匯出實際名稱如 [CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md)的 \< 備註 \> 一節所述。  
  
## 需求  
 **標題:** afxwin.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md)