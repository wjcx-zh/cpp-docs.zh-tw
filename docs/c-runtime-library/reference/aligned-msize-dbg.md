---
title: "_aligned_msize_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_msize_dbg"
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
  - "_aligned_msize_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_msize_dbg"
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _aligned_msize_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回所配置的堆積的記憶體區塊大小 \(僅偵錯版本\)。  
  
## 語法  
  
```  
size_t _aligned_msize_dbg(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### 參數  
 \[in\] `memblock`  
 指向記憶體區塊的指標。  
  
 \[in\] `alignment`  
 對齊值，必須為 2 的整數次方。  
  
 \[in\] `offset`  
 讓記憶體配置強制對齊的位移。  
  
## 傳回值  
 回傳無號整數表示大小 \(以位元組為單位\) 。  
  
## 備註  
 `alignment` 和 `offset` 的值必須與傳遞至配置區塊函式的值相同。  
  
 `_aligned_msize_dbg` 是 [\_aligned\_msize](../../c-runtime-library/reference/aligned-msize.md) 函式的偵錯版本。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，對 `_aligned_msize_dbg` 的每個呼叫會減少為對 `_aligned_msize` 的一個呼叫。  `_aligned_msize` 和 `_aligned_msize_dbg` 都計算基礎堆積的記憶體區塊大小，不過， `_aligned_msize_dbg` 增加偵錯功能:它包括緩衝區記憶體區塊任一邊使用者部分所傳回的大小。  
  
 這個函式會驗證其參數。  如果 `memblock` 為 null 指標或 `alignment` 不是 2 的次方， `_msize` 叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果已處理時，函式將 `errno` 設定成 `EINVAL` 並傳回 \-1 。  
  
 如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型的資訊以及它們的使用方式，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需呼叫標準堆積函式以及偵錯應用程式的偵錯組建的版本之差異的詳細資訊，請參閱 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_msize_dbg`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)