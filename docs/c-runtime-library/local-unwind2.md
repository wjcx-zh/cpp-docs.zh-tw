---
title: "_local_unwind2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_local_unwind2"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_local_unwind2"
  - "local_unwind2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_local_unwind2 函式"
  - "local_unwind2 函式"
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _local_unwind2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內部 CRT 函式。  執行指定範圍資料表中列出的終止處理常式。  
  
## 語法  
  
```  
void _local_unwind2(    PEXCEPTION_REGISTRATION xr,    int stop );  
```  
  
#### 參數  
 \[in\] `xr`  
 與某個範圍資料表相關的註冊記錄。  
  
 \[in\] `stop`  
 指出 `_local_unwind2` 應停止的語彙層級。  
  
## 備註  
 此方法僅用於執行階段環境。  請勿在您的程式碼中呼叫此方法。  
  
 當此方法執行終止處理常式時，會從目前的語彙層級開始進行，直到達到 `stop` 指定的層級為止。  此方法不會執行 `stop` 所指定之層級上的終止處理常式。  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)