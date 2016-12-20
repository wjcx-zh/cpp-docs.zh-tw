---
title: "_aligned_msize | Microsoft Docs"
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
  - "_aligned_msize"
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
  - "_aligned_msize"
  - "aligned_msize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_msize 函式"
  - "aligned_msize 函式"
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_msize
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

回傳堆積中分配的記憶體區塊的大小。  
  
## 語法  
  
```  
size_t _msize(  
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
 `_aligned_msize` 函式回傳呼叫 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_realloc](../../c-runtime-library/reference/aligned-realloc.md) 所配置的記憶體的大小，以位元組為單位。  `alignment` 和 `offset` 的值必須與傳遞至配置區塊函式的值相同。  
  
 當應用程式使用 C 執行期程式庫偵錯版本連結時，`_aligned_msize` 會解析為 [\_aligned\_msize\_dbg](../../c-runtime-library/reference/aligned-msize-dbg.md)。  如需堆積在偵錯過程中的運作，請參閱 [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md) 。  
  
 這個函式會驗證其參數。  如果 `memblock` 為 null 指標或 `alignment` 不是 2 的次方， `_msize` 叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果已處理時，函式將 `errno` 設定成 `EINVAL` 並傳回 \-1 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_msize`|\<malloc.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)