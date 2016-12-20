---
title: "__uncaught_exception | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__uncaught_exception"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__uncaught_exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__uncaught_exception"
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __uncaught_exception
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示一個或多個例外狀況被擲回，但是未由 [try\-catch](../../cpp/try-throw-and-catch-statements-cpp.md) 陳述式的對應 `catch` 區塊處理。  
  
## 語法  
  
```cpp  
bool __uncaught_exception(  
   );  
```  
  
## 傳回值  
 直到符合 `catch` 區塊初始化後，從例外狀況的 `try` 區塊中擲回的時間才為`true` ，否則為 `false`。  
  
## 備註  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_\_uncaught\_exception|eh.h|  
  
## 請參閱  
 [try、throw 和 catch 陳述式 \(C\+\+\)](../../cpp/try-throw-and-catch-statements-cpp.md)