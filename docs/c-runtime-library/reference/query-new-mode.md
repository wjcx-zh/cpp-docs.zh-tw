---
title: "_query_new_mode | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_query_new_mode"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "query_new_mode"
  - "_query_new_mode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_query_new_mode 函式"
  - "處理常式模式"
  - "query_new_mode 函式"
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _query_new_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回 `_set_new_mode` 為 `malloc` 設定的表示新處理模式的整數。  
  
## 語法  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## 傳回值  
 傳回目前 `malloc` 的新處理模式，也就是 0 或 1。  傳回值 1 表示配置記憶體時發生錯誤， `malloc` 呼叫新處理常式常式;傳回值 0 表示成功。  
  
## 備註  
 C\+\+ `_query_new_mode` 函式傳回為 [malloc](../../c-runtime-library/reference/malloc.md) 設定的 C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 函式的表示新處理常式模式的整數。  新的處理常式模式表示，分配記憶體失敗時，`malloc` 是否要呼叫由 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 設定的新處理常式。  根據預設， `malloc` 不會在無法配置記憶體時呼叫新的處理常式。  您可以使用 `_set_new_mode` 覆寫這個行為，讓 `malloc` 失敗時與 **new** 運算子分配記憶體失敗時的相同方式呼叫新處理常式。  如需詳細資訊，請參閱  [operator delete](../../misc/operator-delete-function.md) 和 [operator new](../../misc/operator-new-function.md) 函數於 *C\+\+ Language Reference*。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_query_new_mode`|\<new.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_query\_new\_handler](../../c-runtime-library/reference/query-new-handler.md)