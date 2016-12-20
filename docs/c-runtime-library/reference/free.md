---
title: "free | Microsoft Docs"
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
  - "free"
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
  - "free"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "記憶體區塊, 解除配置"
  - "free 函式"
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# free
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

解除配置或釋放記憶體區塊。  
  
## 語法  
  
```  
void free(   
   void *memblock   
);  
```  
  
#### 參數  
 `memblock`  
 先前要釋放的已配置記憶體區塊。  
  
## 備註  
 `free`函式解除由先前`calloc`, `malloc`或 `realloc`呼叫配置的記憶體區塊 \(`memblock`\)。  釋放的位元組數目與所要求的位元組數目相同，則區塊會配置 \(或重新配置，在 `realloc`的情況下\)。  如果 `memblock` 是 `NULL`，指標會被忽略，且 `free` 會立即傳回。  嘗試釋放無效的指標 \(指向非由 `calloc`, `malloc`或 `realloc`配置的記憶體區塊的指標\) 可能會影響後續配置要求並產生錯誤。  
  
 如果錯誤發生在釋放記憶體， `errno` 設定成作業系統發生錯誤的性質的資訊。  如需詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 在記憶體區塊已經釋放之後， [\_heapmin](../../c-runtime-library/reference/heapmin.md) 會集合未使用的記憶體區域並釋放至作業系統以最小化堆積中未使用的記憶體數量。  不釋放給作業系統的空記憶體會還原至可用記憶體池並可再重新配置。  
  
 當應用程式使用 C 執行期程式庫偵錯版本連結時，`free` 會解析為 [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md)。  如需堆積在偵錯過程中的運作，請參閱 [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md) 。  
  
 `free` 標記為 `__declspec(noalias)`，表示函式保證不會修改全域變數。  如需詳細資訊，請參閱[noalias](../../cpp/noalias.md)。  
  
 若要釋放記憶體配置與 [\_malloca](../../c-runtime-library/reference/malloca.md)，請使用 [\_freea](../../c-runtime-library/reference/freea.md)。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`free`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [malloc](../../c-runtime-library/reference/malloc.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [\_alloca](../../c-runtime-library/reference/alloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [\_freea](../../c-runtime-library/reference/freea.md)