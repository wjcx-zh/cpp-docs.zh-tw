---
title: "_freea | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_freea"
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
  - "freea"
  - "_freea"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_freea 函式"
  - "freea 函式"
  - "記憶體解除配置"
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _freea
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

解除配置或釋放記憶體區塊。  
  
## 語法  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### 參數  
 `memblock`  
 先前要釋放的已配置記憶體區塊。  
  
## 傳回值  
 無。  
  
## 備註  
 `_freea` 函式解除配置由先前呼叫 [\_malloca](../../c-runtime-library/reference/malloca.md)配置的記憶體區塊 \(`memblock`\)。  `_freea` 會檢查記憶體是否位於堆積或堆疊。  如果配置在堆疊上， `_freea` 不會有任何作用。  如果在堆積上配置，釋放的位元組數目與區塊配置時所要求的位元組數目相同。  如果 `memblock` 是 `NULL`，指標會被忽略，且 `_freea` 會立即傳回。  嘗試釋放無效的指標 \(指向非由 `_malloca` 配置的記憶體區塊的指標\) 可能會影響後續配置要求並產生錯誤。  
  
 如果發現記憶體配置於堆積，`freea` 內部呼叫 `free`。  記憶體是否在堆積或堆疊取決於記憶體中在配置記憶體前的位址的標記。  
  
 如果錯誤發生在釋放記憶體， `errno` 設定成作業系統發生錯誤的性質的資訊。  如需詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 在記憶體區塊已經釋放之後， [\_heapmin](../../c-runtime-library/reference/heapmin.md) 會集合未使用的記憶體區域並釋放至作業系統以最小化堆積中未使用的記憶體數量。  不釋放給作業系統的空記憶體會還原至可用記憶體池並可再重新配置。  
  
 對 `_freea` 的呼叫必須隨附於任何 `_malloca` 呼叫。  在相同的記憶體呼叫兩次 `_freea` 也是個錯誤。  當應用程式連結 C 執行階段程式庫的偵錯版本時，特別是 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md) 是藉由定義 `_CRTDBG_MAP_ALLOC`以啟用該功能，可以更簡單地找出遺漏或重複呼叫的 `_freea`。  如需堆積在偵錯過程中的運作，請參閱 [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md) 。  
  
 `_freea` 標記為 `__declspec(noalias)`，表示函式保證不會修改全域變數。  如需詳細資訊，請參閱[noalias](../../cpp/noalias.md)。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_freea`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
 請參閱[\_malloca](../../c-runtime-library/reference/malloca.md)中的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [\_malloca](../../c-runtime-library/reference/malloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_free\_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)