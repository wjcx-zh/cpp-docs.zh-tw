---
title: "_msize_dbg | Microsoft Docs"
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
  - "_msize_dbg"
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
  - "_msize_dbg"
  - "msize_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "記憶體區塊"
  - "_msize_dbg 函式"
  - "msize_dbg 函式"
ms.assetid: a333f4b6-f8a2-4e61-bb69-cb34063b8cef
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _msize_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算的記憶體區塊的大小堆積中 \(僅偵錯版本\)。  
  
## 語法  
  
```  
  
      size_t _msize_dbg(  
   void *userData,  
   int blockType   
);  
```  
  
#### 參數  
 `userData`  
 對記憶體區塊的指標可以決定大小。  
  
 *blockType*  
 指定的記憶體區塊的類型: `_CLIENT_BLOCK` 或 **\_NORMAL\_BLOCK**。  
  
## 傳回值  
 在成功完成， `_msize_dbg` 傳回指定的記憶體區塊的大小 \(以位元組為單位\)；否則會傳回 null。  
  
## 備註  
 `_msize_dbg` 是 \_[msize](../../c-runtime-library/reference/msize.md) 函式的偵錯版本。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，對 `_msize_dbg` 的每個呼叫會減少為對 `_msize` 的一個呼叫。  `_msize` 和 `_msize_dbg` 計算在機處堆積裡的記憶體區塊大小，但是 `_msize_dbg` 加入兩項偵錯功能: 包括緩衝區任一邊使用者部分所傳回記憶體區塊的大小和允許計算特定區塊型別的大小。  
  
 如需在基底堆積的記憶體區塊配置、初始化及管理的方式之偵錯版本的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型的資訊以及它們的使用方式，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需呼叫標準堆積函式以及偵錯應用程式的偵錯組建的版本之差異的詳細資訊，請參閱 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
 這個函式會驗證其參數。  如果 `memblock` 為 null 指標， `_msize` 會叫用無效參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果已處理時，函式將 `errno` 設定成 `EINVAL` 並傳回 \-1 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_msize_dbg`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
  
```  
// crt_msize_dbg.c  
// compile with: /MTd  
/*  
 * This program allocates a block of memory using _malloc_dbg  
 * and then calls _msize_dbg to display the size of that block.  
 * Next, it uses _realloc_dbg to expand the amount of  
 * memory used by the buffer and then calls _msize_dbg again to  
 * display the new amount of memory allocated to the buffer.  
 */  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
        long *buffer, *newbuffer;  
        size_t size;  
  
        /*   
         * Call _malloc_dbg to include the filename and line number  
         * of our allocation request in the header  
         */  
        buffer = (long *)_malloc_dbg( 40 * sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        if( buffer == NULL )  
               exit( 1 );  
  
        /*   
         * Get the size of the buffer by calling _msize_dbg  
         */  
        size = _msize_dbg( buffer, _NORMAL_BLOCK );  
        printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
        /*   
         * Reallocate the buffer using _realloc_dbg and show the new size  
         */  
        newbuffer = _realloc_dbg( buffer, size + (40 * sizeof(long)), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        if( newbuffer == NULL )  
               exit( 1 );  
        buffer = newbuffer;  
        size = _msize_dbg( buffer, _NORMAL_BLOCK );  
        printf( "Size of block after _realloc_dbg of 40 more longs: %u\n", size );  
  
        free( buffer );  
        exit( 0 );  
}  
```  
  
## Output  
  
```  
Size of block after _malloc_dbg of 40 longs: 160  
Size of block after _realloc_dbg of 40 more longs: 320  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)