---
title: "realloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "realloc"
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
  - "_brealloc"
  - "_nrealloc"
  - "realloc"
  - "_frealloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_brealloc 函式"
  - "realloc 函式"
  - "nrealloc 函式"
  - "frealloc 函式"
  - "_nrealloc 函式"
  - "記憶體區塊, 重新配置"
  - "記憶體, 重新配置"
  - "_frealloc 函式"
  - "重新配置記憶體區塊"
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# realloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重新配置記憶體區塊。  
  
## 語法  
  
```  
void *realloc(  
   void *memblock,  
   size_t size   
);  
```  
  
#### 參數  
 `memblock`  
 指向先前配置的記憶體區塊的指標。  
  
 `size`  
 新的大小 \(以位元組為單位\)。  
  
## 傳回值  
 `realloc` 傳回 `void` 指標到重新配置 \(和可捲動\) 的記憶體區塊。  
  
 如果沒有將區塊展開成足夠特定大小的可用記憶體，原始的區塊會保持不變，因此會傳回 `NULL` 。  
  
 如果 `size` 為零，則由 `memblock` 指向的區塊被釋放；傳回的值為 `NULL`，且 `memblock` 會保留指向釋放區塊。  
  
 傳回值指向保證可以儲存任何型別的物件的適當地對齊的儲存空間。  若要得到 `void` 之外的型別指標，請在傳回值上使用型別轉換。  
  
## 備註  
 `realloc` 函式變更配置記憶體區塊的大小。  `memblock` 引數指向記憶體區塊的起始。  如果 `memblock` 是 `NULL`，`realloc` 產生行為與 `malloc`相同，並且配置一個 `size` 位元組的新區塊。  如果 `memblock` 不是 `NULL`，它應該是先前呼叫 `calloc` 所傳回的指標、`malloc`或 `realloc`。  
  
 `size` 引數給區塊以位元組為單位的新大小。  區塊的內容不會由新的短和舊的大小決定變更，不過，新的區塊可以在不同的位置。  由於新的區塊可以在新的記憶體位置，`realloc` 傳回的指標不保證是透過 `memblock` 引數傳遞的指標。  在緩衝區大小上限情況下，`realloc` 最近非零配置記憶體。  
  
 如果記憶體配置失敗，或是要求的記憶體數量超過 `_HEAP_MAXREQ`，則 `realloc` 會將 `errno` 設定為 `ENOMEM`。  如需有關這個錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `realloc`  會呼叫 `malloc` 以使用 C\+\+[\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 函來設定新的處理常式模式。  新的處理常式模式表示，失敗時，`malloc` 是否要呼叫由 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 設定的新處理常式。  根據預設， `malloc` 不會在無法配置記憶體時呼叫新的處理常式。  您可以覆寫這個預設行為，因此，當 `realloc` 無法配置記憶體時，`malloc` 會以 `new` 運算子因相同原因失敗時所執行的相同方式，呼叫新處理常式。  若要覆寫預設值，請呼叫  
  
```  
_set_new_mode(1)  
```  
  
 及早在程式中呼叫，或與 NEWMODE.OBJ 連結 \(請參閱[連結選項](../../c-runtime-library/link-options.md)\)。  
  
 當應用程式使用 C 執行期程式庫偵錯版本連結時，`realloc` 會解析為 [\_realloc\_dbg](../../c-runtime-library/reference/realloc-dbg.md)。  如需堆積在偵錯過程中的運作，請參閱 [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md) 。  
  
 `realloc` 會標示為 `__declspec(noalias)` 和 `__declspec(restrict)`，這表示函式保證不會修改全域變數且傳回的指標不會產生別名。  如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`realloc`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_realloc.c  
// This program allocates a block of memory for  
// buffer and then uses _msize to display the size of that  
// block. Next, it uses realloc to expand the amount of  
// memory used by buffer and then calls _msize again to  
// display the new amount of memory allocated to buffer.  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   long *buffer, *oldbuffer;  
   size_t size;  
  
   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )  
      exit( 1 );  
  
   size = _msize( buffer );  
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );  
  
   // Reallocate and show new size:  
   oldbuffer = buffer;     // save pointer in case realloc fails  
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))   
        ==  NULL )  
   {  
      free( oldbuffer );  // free original block  
      exit( 1 );  
   }  
   size = _msize( buffer );  
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",   
            size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
  **Size of block after malloc of 1000 longs: 4000**  
**Size of block after realloc of 1000 more longs: 8000**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)