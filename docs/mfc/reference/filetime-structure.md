---
title: "FILETIME 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FILETIME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FILETIME 結構"
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# FILETIME 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`FILETIME` 結構是表示 100 奈秒間隔數 64 位元值是從 1601 年 1 月 1 日。  
  
## 語法  
  
```  
  
      typedef struct _FILETIME {  
   DWORD dwLowDateTime;   /* low 32 bits  */  
   DWORD dwHighDateTime;  /* high 32 bits */  
} FILETIME, *PFILETIME, *LPFILETIME;  
```  
  
#### 參數  
 *dwLowDateTime*  
 指定檔案時間的 32 個低位元。  
  
 *dwHighDateTime*  
 指定檔案時間的高 32 位元。  
  
## 需求  
 **標頭 :** windef.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../Topic/CTime::CTime.md)