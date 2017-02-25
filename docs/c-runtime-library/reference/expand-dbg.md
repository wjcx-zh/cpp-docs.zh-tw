---
title: "_expand_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_expand_dbg"
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
  - "expand_dbg"
  - "_expand_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "記憶體區塊，變更大小"
  - "expand_dbg 函式"
  - "_expand_dbg 函式"
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _expand_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以展開或壓縮區塊調整在堆積上配置指定的記憶體區塊 \(僅偵錯版本\)。  
  
## 語法  
  
```  
void *_expand_dbg(   
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### 參數  
 `userData`  
 指向先前配置的記憶體區塊的指標。  
  
 `newSize`  
 重新配置區塊 \(位元組\) 新要求的大小。  
  
 `blockType`  
 調整大小的區塊所要求的型別: `_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 指向要求的展開作業或 `NULL` 的來源檔案名稱的指標。  
  
 `linenumber`  
 展開作業為要求或`NULL`的原始程式檔行號。  
  
 `filename` 和 `linenumber` 參數只有在 `_expand_dbg` 已經明確呼叫或 [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 前置處理器常數已經被定義後才可使用。  
  
## 傳回值  
 在成功完成時， `_expand_dbg` 會傳回調整記憶體區塊大小的指標。  由於記憶體不會移動，位址與 userData 相同。  如果發生錯誤或區塊無法展開至要求的大小，則會傳回 `NULL`。  如果失敗， `errno` 是作業系統失敗性質的相關資訊。  如需 `errno` 的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_expand_dbg` 函式是 \_[expand](../../c-runtime-library/reference/expand.md) 函式的偵錯版本。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，對 `_expand_dbg`  的每個呼叫會減少對 `_expand` 的一個呼叫。  `_expand`  和 `_expand_dbg`  皆在基底堆積調整一個記憶體區塊大小，不過 `_expand_dbg` 搭載幾個偵錯功能：在使用者部分的區塊內其中一邊的緩衝區，可測試遺漏；可追蹤特定配置型別的區塊類型參數；決定配置要求的原點之 `filename`\/`linenumber` 資訊。  
  
 `_expand_dbg` 會調整大小給特定的記憶體區塊比要求的 `newSize` 更多空間。  `newSize` 可能大於或小於最初配置的記憶體區塊之大小。  偵錯堆積管理員用額外空間來連接偵錯記憶體區塊，並提供應用程式偵錯標頭資訊並覆寫緩衝區。  調整大小以完成展開或壓縮原始記憶體區塊。  `_expand_dbg` 不會移動記憶體區塊，如 [\_realloc\_dbg](../../c-runtime-library/reference/realloc-dbg.md) 函式。  
  
 當 `newSize` 大於原始區塊大小時，記憶體區塊展開。  在增益集期間，如果記憶體區塊無法以容納要求的大小擴充，則會傳回 `NULL` 。  當 `newSize` 小於原始區塊大小時，記憶體區塊會縮小，直到新大小取得。  
  
 如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型的資訊以及它們的使用方式，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需呼叫標準堆積函式以及偵錯應用程式的偵錯組建的版本之差異的詳細資訊，請參閱 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
 這個函式會驗證它的參數。  如果 `memblock` 為 null 指標，或如果大小大於 `_HEAP_MAXREQ`，這個函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `NULL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_expand_dbg`|\<crtdbg.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
  
```  
// crt_expand_dbg.c  
//  
// This program allocates a block of memory using _malloc_dbg  
// and then calls _msize_dbg to display the size of that block.  
// Next, it uses _expand_dbg to expand the amount of  
// memory used by the buffer and then calls _msize_dbg again to  
// display the new amount of memory allocated to the buffer.  
//  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   long *buffer;  
   size_t size;  
  
   // Call _malloc_dbg to include the filename and line number  
   // of our allocation request in the header  
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if( buffer == NULL )  
      exit( 1 );  
  
   // Get the size of the buffer by calling _msize_dbg  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
   // Expand the buffer using _expand_dbg and show the new size  
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
   if( buffer == NULL )  
      exit( 1 );  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",  
           size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
  **Size of block after \_malloc\_dbg of 40 longs: 160**  
**Size of block after \_expand\_dbg of 1 more long: 164**   
## 註解  
 這個程式的輸出取決於電腦展開所有部分的能力。  如果所有部分展開，輸出會顯示在輸出區域反映。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)