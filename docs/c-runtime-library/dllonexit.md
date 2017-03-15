---
title: "__dllonexit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__dllonexit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr120_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__dllonexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__dllonexit"
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# __dllonexit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

註冊要呼叫的常式結束時間。  
  
## 語法  
  
```  
_onexit_t __dllonexit(  
   _onexit_t func,  
   _PVFV **  pbegin,   
   _PVFV **  pend   
   )  
```  
  
#### 參數  
 `func`  
 in 要執行的函式的指標在匯出。  
  
 `pbegin`  
 在中斷連結指向函式清單開始執行之變數的指標。  
  
 `pend`  
 在中斷連結指向函式清單結束執行之變數的指標。  
  
## 傳回值  
 如果成功，指標對使用者的函式。  否則， null 指標。  
  
## 備註  
 `__dllonexit` 函式類似於 [\_onexit](../c-runtime-library/reference/onexit-onexit-m.md) 函式，但是該函式使用的全域變數不會看見這個常式。  而不是全域變數，這個函式會使用 `pbegin` 和 `pend` 參數。  
  
 在與 MSVCRT.LIB 連結的 DLL 的 `_onexit` 和 `atexit` 函式必須維護自己的 atexit\/\_onexit 清單。  這個常式是這類 DLL 呼叫的背景工作。  
  
 `_PVFV`型別被定義為 `typedef void (__cdecl *_PVFV)(void)`。  
  
## 需求  
  
|常式|必要檔案|  
|--------|----------|  
|\_\_dllonexit|onexit.c|  
  
## 請參閱  
 [\_onexit，\_onexit\_m](../c-runtime-library/reference/onexit-onexit-m.md)