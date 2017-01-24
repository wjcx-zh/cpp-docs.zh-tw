---
title: "_msize | Microsoft Docs"
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
  - "_msize"
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
  - "msize"
  - "_msize"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_msize 函式"
  - "記憶體區塊"
  - "msize 函式"
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _msize
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

回傳堆積中分配的記憶體區塊的大小。  
  
## 語法  
  
```  
  
      size_t _msize(  
   void *memblock   
);  
```  
  
#### 參數  
 `memblock`  
 指向記憶體區塊的指標。  
  
## 傳回值  
 `_msize` 回傳無號整數表示大小 \(以位元組為單位\) 。  
  
## 備註  
 `_msize` 函式回傳呼叫 `calloc` 、 `malloc` 或 `realloc` 所配置的記憶體的大小，以位元組為單位。  
  
 當應用程式與 C 執行期程式庫的偵錯版本連結時， `_msize` 會變成 [\_msize\_dbg](../../c-runtime-library/reference/msize-dbg.md) 。  如需堆積在偵錯過程中的運作，請參閱 [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md) 。  
  
 這個函式會驗證其參數。  如果 `memblock` 為 null 指標， `_msize` 會叫用無效參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果已處理時，函式將 `errno` 設定成 `EINVAL` 並傳回 \-1 。  
  
## 需求  
  
|程序|必要的標頭檔|  
|--------|------------|  
|`_msize`|\<malloc.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 所有的 [C 執行階段程式庫 \(C run\-time libraries\)](../../c-runtime-library/crt-library-features.md) 版本。  
  
## 範例  
 請參閱 [realloc](../../c-runtime-library/reference/realloc.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需更多的資訊，請參閱 [平台調用範例 \(Platform Invoke Examples\)](../Topic/Platform%20Invoke%20Examples.md) 。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [\_expand](../../c-runtime-library/reference/expand.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)