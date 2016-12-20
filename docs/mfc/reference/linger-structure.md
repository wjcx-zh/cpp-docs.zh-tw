---
title: "LINGER 結構 | Microsoft Docs"
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
  - "LINGER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LINGER 結構"
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINGER 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`LINGER` 結構的支援 `CAsyncSocket::GetSockOpt`的 **SO\_LINGER** 和 **SO\_DONTLINGER** 選項使用。  
  
## 語法  
  
```  
  
      struct linger {  
   u_short l_onoff;            // option on/off  
   u_short l_linger;           // linger time  
};  
```  
  
## 備註  
 設定 **SO\_DONTLINGER** 選項導致封鎖在成員函式 **Close** ，在等待未傳送的資料傳輸時。  設定這個選項會設定 **SO\_LINGER** 相等和 **l\_onoff** 設為 0。  
  
## 需求  
 **標頭：**winsock2.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CAsyncSocket::GetSockOpt](../Topic/CAsyncSocket::GetSockOpt.md)   
 [CAsyncSocket::SetSockOpt](../Topic/CAsyncSocket::SetSockOpt.md)