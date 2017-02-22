---
title: "_aligned_malloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_malloc_dbg"
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
  - "_aligned_malloc_dbg"
  - "aligned_malloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_malloc_dbg 函式"
  - "aligned_malloc_dbg 函式"
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _aligned_malloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用額外空間為偵錯標頭及覆寫緩衝區，依指定的對齊界限配置記憶體 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
void * _aligned_malloc_dbg(     size_t size,      size_t alignment,    const char *filename,    int linenumber  );  
```  
  
#### 參數  
 \[in\] `size`  
 要求的記憶體配置的大小。  
  
 \[in\] `alignment`  
 對齊值，必須是 2 的整數冪。  
  
 \[in\] `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 NULL。  
  
 \[in\] `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 NULL。  
  
## 傳回值  
 已配置之記憶體區塊的指標，或為 `NULL` \(作業失敗時\)。  
  
## 備註  
 `_aligned_malloc_dbg` 是偵錯版本的 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 函式。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，每個 `_aligned_malloc_dbg` 的呼叫會降至 `_aligned_malloc` 的呼叫。  `_aligned_malloc` 和 `_aligned_malloc_dbg` 都會配置基底堆積中的記憶體區塊，但 `_aligned_malloc_dbg` 還提供數種偵錯功能：在區塊的使用者部分的任一端使用緩衝區以測試遺漏，以及判斷配置要求來源的 `filename`\/`linenumber` 資訊。  
  
 `_aligned_malloc_dbg` 會使用比要求的 `size` 稍多一些的空間配置記憶體區塊。  偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。  區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。  
  
 若記憶體配置失敗，或是所需的記憶體數量 \(包含之前提到的額外負荷\) 超過 `_HEAP_MAXREQ`，`_aligned_malloc_dbg` 會將 `errno` 設定為 `ENOMEM`。  如需此錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外，`_aligned_malloc_dbg` 也會驗證其參數。  若 `alignment` 不是 2 的冪，或是 `size` 為零，則此函式會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  若允許繼續執行，此函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
 如需在偵錯版本的基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型以及如何使用它們的詳細資訊，請參閱[偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_malloc_dbg`|\<crtdbg.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)