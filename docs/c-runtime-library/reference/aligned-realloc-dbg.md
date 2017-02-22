---
title: "_aligned_realloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_realloc_dbg"
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
  - "aligned_realloc_dbg"
  - "_aligned_realloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_realloc_dbg 函式"
  - "aligned_realloc_dbg 函式"
ms.assetid: 8aede920-991e-44cd-867f-83dc2165db47
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _aligned_realloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變更使用 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
void * _aligned_realloc_dbg(    void *memblock,     size_t size,     size_t alignment,    const char *filename,    int linenumber  );  
```  
  
#### 參數  
 \[in\] `memblock`  
 目前記憶體區塊指標。  
  
 \[in\] `size`  
 要求的記憶體配置的大小。  
  
 \[in\] `alignment`  
 對齊值，必須是 2 的整數冪。  
  
 \[in\] `filename`  
 要求 `realloc` 作業之原始程式檔的名稱的指標，或為 NULL。  
  
 \[in\] `linenumber`  
 原始程式檔中的行號，其中要求 `realloc` 作業，或為 NULL。  
  
## 傳回值  
 `_aligned_realloc_dbg` 會傳回重新配置後 \(且可能有移動\) 記憶體區塊的 Void 指標。  若大小為 0，且緩衝區引數不是 `NULL`，則傳回值為 `NULL`，或者，若沒有足夠的可用記憶體將區塊展開為指定大小，傳回值也會是 NULL。  在第一種情況中，會釋放原始區塊。  在第二種情況中，原始區塊會保留不變。  儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。  若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。  
  
 重新配置記憶體並變更區塊的對齊是不對的。  
  
## 備註  
 `_aligned_realloc_dbg` 是偵錯版本的 [\_aligned\_realloc](../../c-runtime-library/reference/aligned-realloc.md) 函式。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，每個 `_aligned_realloc_dbg` 的呼叫會降至 \_`aligned_realloc` 的呼叫。  \_`aligned_realloc`和 `_aligned_realloc_dbg` 都會重新配置基底堆積中的記憶體區塊，但 `_aligned_realloc_dbg` 還容納數種偵錯功能：在區塊的使用者部分的任一端使用緩衝區以測試遺漏，以及追蹤特定配置類型的區塊類型參數，還有判斷配置要求來源的 `filename`\/`linenumber` 資訊。  
  
 `_aligned_realloc_dbg` 會使用比要求的 `newSize` 稍多一些的空間重新配置指定的記憶體區塊。  `newSize` 可能會比原始配置的記憶體區塊大小更多或更少。  偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。  重新配置可能會導致將原始記憶體區塊移到堆積中的不同位置，也可能會變更記憶體區塊的大小。  若記憶體區塊已移動，則會覆寫原始區塊的內容。  
  
 若記憶體配置失敗，或是所需的記憶體數量 \(包含之前提到的額外負荷\) 超過 `_HEAP_MAXREQ`，`_aligned_realloc_dbg` 會將 `errno` 設定為 `ENOMEM`。  如需此錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 此外，`_aligned_realloc_dbg` 也會驗證其參數。  若 `alignment` 不是 2 的冪，則此函式會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  若允許繼續執行，此函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
 如需在偵錯版本的基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型以及如何使用它們的詳細資訊，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_realloc_dbg`|\<crtdbg.h\>|  
  
 如需相容性詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)