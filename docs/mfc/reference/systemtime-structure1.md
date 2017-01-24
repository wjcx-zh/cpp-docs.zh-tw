---
title: "SYSTEMTIME 結構 | Microsoft Docs"
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
  - "SYSTEMTIME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SYSTEMTIME 結構"
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SYSTEMTIME 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`SYSTEMTIME` 結構使用月、日、年、週間日、小時、分鐘、秒和毫秒數的個別成員，代表日期與時間。  
  
## 語法  
  
```  
  
      typedef struct _SYSTEMTIME {  
   WORD wYear;  
   WORD wMonth;  
   WORD wDayOfWeek;  
   WORD wDay;  
   WORD wHour;  
   WORD wMinute;  
   WORD wSecond;  
   WORD wMilliseconds;  
} SYSTEMTIME;  
```  
  
#### 參數  
 *wYear*  
 目前的年度。  
  
 *wMonth*  
 目前月份；一月為 1。  
  
 *wDayOfWeek*  
 目前星期幾：星期日是 0、星期一是 1，依此類推。  
  
 *wDay*  
 月份的目前日期。  
  
 *wHour*  
 目前小時。  
  
 *wMinute*  
 目前的分鐘。  
  
 *wSecond*  
 目前的秒數。  
  
 *wMilliseconds*  
 目前毫秒。  
  
## 範例  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/CPP/systemtime-structure1_1.cpp)]  
  
## 需求  
 **標頭：**winbase.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../Topic/CTime::CTime.md)