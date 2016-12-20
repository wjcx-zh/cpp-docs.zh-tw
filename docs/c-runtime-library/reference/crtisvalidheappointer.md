---
title: "_CrtIsValidHeapPointer | Microsoft Docs"
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
  - "_CrtIsValidHeapPointer"
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
  - "CrtlsValidHeapPointer"
  - "_CrtIsValidHeapPointer"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtIsValidHeapPointer 函式"
  - "CrtIsValidHeapPointer 函式"
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtIsValidHeapPointer
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

確認指定的指標是在某個 C 執行階段程式庫所配置的堆積中，但呼叫端的 CRT 程式庫不一定需要。  在 Visual Studio 2010 之前的 CRT 版本中，這會確認指定的指標是在本機堆積中 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
  
        int _CrtIsValidHeapPointer(   
   const void *userData   
);  
```  
  
#### 參數  
 `userData`  
 所配置記憶體區塊開頭的指標。  
  
## 傳回值  
 如果指定的指標是在所有 CRT 程式庫執行個體所共用的堆積中，則 `_CrtIsValidHeapPointer` 會傳回 TRUE。  在 Visual Studio 2010 之前的 CRT 版本中，這會確認指定的指標是在本機堆積中 \(僅限偵錯版本\)。  否則，此函式會傳回 FALSE。  
  
## 備註  
 不建議您使用這個函式。  從 Visual Studio 2010 CRT 程式庫開始，所有 CRT 程式庫都會共用一個 OS 堆積 \(*「處理序堆積」*\(Process Heap\)。  `_CrtIsValidHeapPointer` 函式會報告是否已在 CRT 堆積中配置指標，而不是由呼叫端的 CRT 程式庫配置它。  例如，請考慮使用 CRT 程式庫的 Visual Studio 2010 版本所配置的區塊。  如果 CRT 程式庫的 Visual Studio 2012 版本所匯出的 `_CrtIsValidHeapPointer` 函式測試指標，則會傳回 TRUE。  這不再是有用的測試。  在 Visual Studio 2010 之前的 CRT 程式庫版本中，此函式用來確定特定記憶體位址是在本機堆積中。  本機堆積指的是 C 執行階段程式庫的特定執行個體所建立和管理的堆積。  如果動態連結程式庫 \(DLL\) 包含與執行階段程式庫的靜態連結，則會有執行階段堆積的專屬執行個體，因此有其專屬堆積，而與應用程式的本機堆積無關。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，會在前置處理期間移除 `_CrtIsValidHeapPointer` 的呼叫。  
  
 因為此函式會傳回 TRUE 或 FALSE，所以可將該函式傳遞至其中一個 [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。  如果指定的位址不在本機堆積內，則下列範例會造成判斷提示失敗：  
  
```  
_ASSERTE( _CrtIsValidHeapPointer( userData ) );  
```  
  
 如需如何搭配使用 `_CrtIsValidHeapPointer` 與其他偵錯函式和巨集的詳細資訊，請參閱[報告巨集](../Topic/Macros%20for%20Reporting.md)。  如需如何在偵錯版本的基底堆積中配置、初始化和管理記憶體區塊的相關資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtIsValidHeapPointer`|\<crtdbg.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## 範例  
 下列範例示範如何測試記憶體在與 Visual Studio 2010 之前的 C 執行階段程式庫搭配使用時是否有效。  這個範例是針對舊版 CRT 程式庫程式碼的使用者所提供。  
  
```  
// crt_isvalid.c  
/*  
 * This program allocates a block of memory using _malloc_dbg  
 * and then tests the validity of this memory by calling   
 * _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
#define  TRUE   1  
#define  FALSE  0  
  
int main( void )  
{  
        char *my_pointer;  
  
        /*   
         * Call _malloc_dbg to include the filename and line number  
         * of our allocation request in the header information  
         */  
        my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,   
        _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
        // Ensure that the memory got allocated correctly  
        _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,   
        NULL, NULL, NULL );  
  
         // Test for read/write accessibility  
        if (_CrtIsValidPointer((const void *)my_pointer,   
        sizeof(char) * 10, TRUE))  
                printf("my_pointer has read and write accessibility.\n");  
        else  
                printf("my_pointer only has read access.\n");  
  
        // Make sure my_pointer is within the local heap  
        if (_CrtIsValidHeapPointer((const void *)my_pointer))  
                printf("my_pointer is within the local heap.\n");  
        else  
                printf("my_pointer is not located within the local"  
                       " heap.\n");  
  
        free(my_pointer);  
}  
```  
  
## 輸出  
  
```  
my_pointer has read and write accessibility.  
my_pointer is within the local heap.  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)