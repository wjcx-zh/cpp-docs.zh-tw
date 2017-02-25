---
title: "_abnormal_termination | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_abnormal_termination"
apilocation: 
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_abnormal_termination"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_abnormal_termination"
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# _abnormal_termination
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 [try\-finally 陳述式](../cpp/try-finally-statement.md) 的 `__finally` 區塊是編碼，當系統執行終止處理常式一份內部清單中。  
  
## 語法  
  
```cpp  
int   _abnormal_termination(  
   );  
```  
  
## 傳回值  
 如果系統 *回溯* 堆疊則為`true`，;否則為 `false`。  
  
## 備註  
 這是用來將內部功能處理回溯例外狀況並不適合從使用者程式碼呼叫。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_abnormal\_termination|excpt.h|  
  
## 請參閱  
 [try\-finally 陳述式](../cpp/try-finally-statement.md)