---
title: "_recalloc | Microsoft Docs"
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
  - "_recalloc"
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
  - "_recalloc"
  - "recalloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_recalloc 函式"
  - "recalloc 函式"
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _recalloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`realloc` 和 `calloc` 的組合。  重新配置在記憶體中建立陣列並初始化其元素為 0。  
  
## 語法  
  
```  
void *_recalloc(   
   void *memblock  
   size_t num,  
   size_t size   
);  
```  
  
#### 參數  
 `memblock`  
 指向先前配置的記憶體區塊的指標。  
  
 `num`  
 項目數。  
  
 `size`  
 每個項目的位元組長度。  
  
## 傳回值  
 `_recalloc` 傳回 `void` 指標到重新配置 \(和可捲動\) 的記憶體區塊。  
  
 如果沒有將區塊展開成足夠特定大小的可用記憶體，原始的區塊會保持不變，因此會傳回 `NULL` 。  
  
 如果要求的大小為零，則被 `memblock` 指向的區塊被釋放；傳回值為 `NULL`，且 `memblock` 會保留指向其釋放區塊。  
  
 傳回值指向保證可以儲存任何型別的物件的適當地對齊的儲存空間。  若要得到 `void` 之外的型別指標，請在傳回值上使用型別轉換。  
  
## 備註  
 \_`recalloc` 函式變更配置記憶體區塊的大小。  對記憶體區塊的起始 `memblock` 引數指向記憶體區塊的起始。  如果 `memblock` 是 `NULL`，`recalloc` \) 產生行為與 [calloc](../../c-runtime-library/reference/calloc.md)相同，並且配置一個 `num` \* `size` 位元組的新區塊。  每個元素初始化為 0。  如果 `memblock` 不是 `NULL`，它應該是先前呼叫 `calloc` 所傳回的指標、[malloc](../../c-runtime-library/reference/malloc.md)或 [realloc](../../c-runtime-library/reference/realloc.md)。  
  
 由於新的區塊可以在新的記憶體位置，`recalloc` 傳回的指標不保證是透過 `memblock` 引數傳遞的指標。  
  
 如果記憶體配置失敗，或是要求的記憶體數量超過 `_HEAP_MAXREQ`，則 `_recalloc` 會將 `errno` 設定為 `ENOMEM`。  如需有關這個錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `recalloc` 會呼叫 `realloc` 以使用 C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 函來設定新的處理常式模式。  新的處理常式模式表示，失敗時，`realloc` 是否要呼叫由 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 設定的新處理常式。  根據預設， `realloc` 不會在無法配置記憶體時呼叫新的處理常式。  您可以覆寫這個預設行為，因此，當 `recalloc` 無法配置記憶體時，`realloc` 會以 `new` 運算子因為相同原因失敗時的相同方式，呼叫新處理常式。  若要覆寫預設值，請呼叫  
  
```  
_set_new_mode(1)  
```  
  
 及早在您的程式中呼叫，或與 NEWMODE.OBJ 連結。  
  
 當應用程式使用 C 執行期程式庫偵錯版本連結時，`recalloc` 會解析為 [\_recalloc\_dbg](../../c-runtime-library/reference/recalloc-dbg.md)。  如需堆積在偵錯過程中的運作，請參閱 [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md) 。  
  
 `_recalloc` 會標示為 `__declspec(noalias)` 和 `__declspec(restrict)`，這表示函式保證不會修改全域變數且傳回的指標不會產生別名。  如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_recalloc`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [\_recalloc\_dbg](../../c-runtime-library/reference/recalloc-dbg.md)   
 [\_aligned\_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)   
 [\_aligned\_offset\_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [連結選項](../../c-runtime-library/link-options.md)