---
title: "_malloc_dbg | Microsoft Docs"
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
  - "_malloc_dbg"
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
  - "malloc_dbg"
  - "_malloc_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_malloc_dbg 函式"
  - "malloc_dbg 函式"
  - "記憶體配置"
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _malloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用額外空間為偵錯標頭及覆寫緩衝區配置堆積中的記憶體區塊 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
void *_malloc_dbg(    size_t size,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### 參數  
 `size`  
 要求的記憶體區塊大小 \(位元組\)。  
  
 `blockType`  
 要求的記憶體區塊類型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 NULL。  
  
 `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 NULL。  
  
 只有在已明確呼叫 `_malloc_dbg`，或是已定義 [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 處理器常數時，才可以使用 `filename` 和 `linenumber` 參數。  
  
## 傳回值  
 成功完成時，此函式會傳回重新配置記憶體區塊後的使用者部分的指標，呼叫新的處理常式函式，或是傳回 NULL。  如需傳回行為的完整說明，請參閱下列＜備註＞一節。  如需如何使用新的處理常式函式的詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md) 函式。  
  
## 備註  
 `_malloc_dbg` 是偵錯版本的 [malloc](../../c-runtime-library/reference/malloc.md) 函式。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，每個 `_malloc_dbg` 的呼叫會降至 `malloc` 的呼叫。  `malloc` 和 `_malloc_dbg` 都會配置基底堆積中的記憶體區塊，但 `_malloc_dbg` 還提供數種偵錯功能：在區塊的使用者部分的任一端使用緩衝區以測試遺漏，以及追蹤特定配置類型的區塊類型參數，還有判斷配置要求來源的 `filename`\/`linenumber` 資訊。  
  
 `_malloc_dbg` 會使用比要求的 `size` 稍多一些的空間配置記憶體區塊。  偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。  區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。  
  
 若記憶體配置失敗，或是所需的記憶體數量 \(包含之前提到的額外負荷\) 超過 `_HEAP_MAXREQ`，`_malloc_dbg` 會將 `errno` 設定為 `ENOMEM`。  如需此錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如需在偵錯版本的基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型以及如何使用它們的詳細資訊，請參閱[偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_malloc_dbg`|\<crtdbg.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## 範例  
 如需使用 `_malloc_dbg` 的範例，請參閱 [crt\_dbg1](http://msdn.microsoft.com/zh-tw/17b4b20c-e849-48f5-8eb5-dca6509cbaf9)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_calloc\_dbg](../../c-runtime-library/reference/calloc-dbg.md)   
 [\_calloc\_dbg](../../c-runtime-library/reference/calloc-dbg.md)