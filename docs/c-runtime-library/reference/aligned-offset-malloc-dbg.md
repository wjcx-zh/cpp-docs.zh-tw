---
title: "_aligned_offset_malloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_offset_malloc_dbg"
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
  - "_aligned_offset_malloc_dbg"
  - "aligned_offset_malloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_offset_malloc_dbg 函式"
  - "aligned_offset_malloc_dbg 函式"
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_offset_malloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定的對齊界限內配置記憶體 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
void * _aligned_offset_malloc_dbg(  
   size_t size,   
   size_t alignment,   
   size_t offset,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### 參數  
 \[in\] `size`  
 要求的記憶體配置大小。  
  
 \[in\] `alignment`  
 對齊值，必須為 2 的整數次方。  
  
 \[in\] `offset`  
 讓記憶體配置強制對齊的位移。  
  
 \[in\] `filename`  
 指向要求配置作業或空（NULL）的來源檔案名稱之指標。  
  
 \[in\] `linenumber`  
 配置作業為要求或空的原始程式檔行號。  
  
## 傳回值  
 指向配置的記憶體區塊之指標。若作業失敗則為 `NULL` 。  
  
## 備註  
 `_aligned_offset_malloc_dbg` 是 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 函式的偵錯版本。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，對 `_aligned_offset_malloc_dbg` 的每個呼叫會減少為對 `_aligned_offset_malloc` 的一個呼叫。  `_aligned_offset_malloc` 和 `_aligned_offset_malloc_dbg` 皆在基底堆積配置一個記憶體區塊，不過 `_aligned_offset_malloc_dbg` 提供幾個偵錯功能：在使用者部分的區塊內其中一邊的緩衝區，可測試遺漏；可追蹤特定配置型別的區塊類型參數；決定配置要求的原點之 `filename`\/`linenumber` 資訊。  
  
 `_aligned_offset_malloc_dbg` 會配置比要求的 `size` 更多空間的記憶體區塊。  偵錯堆積管理員用額外空間來連接偵錯記憶體區塊，並提供應用程式偵錯標頭資訊並覆寫緩衝區。  當區塊被配置時，區塊的使用者部分會被填入 0xCD 值，而且每個覆寫緩衝區會填入 0xFD。  
  
 `_aligned_offset_malloc_dbg` 適用於在巢狀項目需要對齊的情況；例如，如果在巢狀類別需要對齊時。  
  
 `_aligned_offset_malloc_dbg` 是根據 `malloc`；如需詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 如果記憶體配置失敗或者要求大小大於 `_HEAP_MAXREQ`，這個函式會將 `errno` 設為 `ENOMEM`。  如需 `errno` 的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  此外， `_aligned_offset_malloc` 會驗證其參數。  如果 `alignment` 不是 2 的次方，或 `offset` 大於或等於 `size` 並且不是零，這個函式會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這個函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
 如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 如需配置區塊類型的資訊以及它們的使用方式，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_offset_malloc_dbg`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)