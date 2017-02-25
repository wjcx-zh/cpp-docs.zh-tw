---
title: "_calloc_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_calloc_dbg"
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
  - "_calloc_dbg"
  - "calloc_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_calloc_dbg 函式"
  - "calloc_dbg 函式"
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _calloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在堆積中配置數個記憶體區塊，與偵錯標題和重新寫入緩衝區的額外空間 \(僅偵錯版本\)。  
  
## 語法  
  
```  
void *_calloc_dbg(   
   size_t num,  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### 參數  
 `num`  
 記憶體區塊要求數目。  
  
 `size`  
 每個記憶體區塊 \(位元組\) 的要求大小。  
  
 `blockType`  
 記憶體區塊的要求型別：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 如需配置區塊類型的資訊以及它們的使用方式，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
 `filename`  
 指向要求配置作業或 `NULL` 的來源檔案名稱之指標。  
  
 `linenumber`  
 配置作業為要求或 `NULL` 的原始程式檔行號。  
  
 `filename` 和 `linenumber` 參數只有在 `_calloc_dbg` 已經明確呼叫或 [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 前置處理器常數已經被定義後才可使用。  
  
## 傳回值  
 在成功完成後，這個函式會傳回指向上次配置的記憶體區塊的使用者部分的指標、呼叫新處理常式函式、或傳回 `NULL`。  如需傳回行為的完整說明，請參閱備註章節。  如需使用新處理常式函式的詳細資訊，請參閱 [calloc](../../c-runtime-library/reference/calloc.md) 函式。  
  
## 備註  
 `_calloc_dbg` 是 [calloc](../../c-runtime-library/reference/calloc.md) 函式的偵錯版本。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，對 `_calloc_dbg` 的每個呼叫會減少為對 `calloc` 的一個呼叫。  `calloc` 和 `_calloc_dbg` 會在基底堆積配置 `num` 記憶體區塊，不過 `_calloc_dbg` 提供幾個偵錯功能：  
  
-   在測試遺漏的區塊的任一邊使用者部分進行緩衝。  
  
-   追蹤特定配置類型的區塊類型參數。  
  
-   決定配置要求原點的 `filename`\/`linenumber` 資訊。  
  
 `_calloc_dbg` 配置給每個記憶體區塊的空間會比要求的 `size` 更多一些。  偵錯堆積管理員用額外空間來連接偵錯記憶體區塊，並提供應用程式偵錯標頭資訊並覆寫緩衝區。  當區塊被配置時，區塊的使用者部分會被填入 0xCD 值，而且每個覆寫緩衝區會填入 0xFD。  
  
 如果記憶體配置失敗，`_calloc_dbg` 會將 `errno` 設至 `ENOMEM` ；如果需要的記憶體數量 \(先前提到的包括額外負荷\) 超過 `_HEAP_MAXREQ`，`EINVAL` 會傳回。  如需有關這個錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需呼叫標準堆積函式以及偵錯應用程式的偵錯組建的版本之差異的詳細資訊，請參閱 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_calloc_dbg`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_callocd.c  
/*  
 * This program uses _calloc_dbg to allocate space for  
 * 40 long integers. It initializes each element to zero.  
 */  
#include <stdio.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
        long *bufferN, *bufferC;  
  
        /*   
         * Call _calloc_dbg to include the filename and line number  
         * of our allocation request in the header and also so we can  
         * allocate CLIENT type blocks specifically  
         */  
        bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );  
        if( bufferN != NULL && bufferC != NULL )  
              printf( "Allocated memory successfully\n" );  
        else  
              printf( "Problem allocating memory\n" );  
  
        /*   
         * _free_dbg must be called to free CLIENT type blocks  
         */  
        free( bufferN );  
        _free_dbg( bufferC, _CLIENT_BLOCK );  
}  
```  
  
  **成功配置記憶體**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [\_DEBUG](../../c-runtime-library/debug.md)