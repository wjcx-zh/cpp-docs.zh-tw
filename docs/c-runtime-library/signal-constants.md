---
title: "signal 常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SIGTERM"
  - "SIGFPE"
  - "SIGABRT"
  - "SIGILL"
  - "SIGINT"
  - "SIGSEGV"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SIGABRT 常數"
  - "SIGFPE 常數"
  - "SIGILL 常數"
  - "SIGINT 常數"
  - "signal 常數"
  - "SIGSEGV 常數"
  - "SIGTERM 常數"
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# signal 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
#include <signal.h>  
```  
  
## 備註  
 `sig` 引數必須是下列其中一個資訊清單常數 \(定義於 SIGNAL.H\)。  
  
 `SIGABRT`  
 異常終止  預設動作以結束代碼 3. 的呼叫端。  
  
 `SIGABRT_COMPAT`  
 和 SIGABRT 相同。  為了與其他平台的相容性。  
  
 `SIGFPE`  
 浮點錯誤，例如溢位、除以零或無效的作業。  預設動作結束呼叫端。  
  
 `SIGILL`  
 不合法的指令。  預設動作結束呼叫端。  
  
 `SIGINT`  
 CTRL\+C 中斷。  預設動作以結束代碼 3. 的呼叫端。  
  
 `SIGSEGV`  
 不合法的儲存體存取。  預設動作結束呼叫端。  
  
 `SIGTERM`  
 終止要求傳送至程式。  預設動作以結束代碼 3. 的呼叫端。  
  
 `SIG_ERR`  
 這個錯誤的信號的傳回型別時發生。  
  
## 請參閱  
 [signal](../c-runtime-library/reference/signal.md)   
 [raise](../c-runtime-library/reference/raise.md)   
 [全域常數](../c-runtime-library/global-constants.md)