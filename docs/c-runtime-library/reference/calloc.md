---
title: "calloc | Microsoft Docs"
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
  - "calloc"
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
  - "calloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "記憶體配置, 陣列"
  - "calloc 函式"
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# calloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

配置在記憶體中陣列的元素初始化為 0。  
  
## 語法  
  
```  
void *calloc(   
   size_t num,  
   size_t size   
);  
```  
  
#### 參數  
 `num`  
 項目數。  
  
 `size`  
 每個項目的位元組長度。  
  
## 傳回值  
 `calloc` 將指標傳回這個配置的空間。  傳回值指向的儲存空間保證可以儲存任何型別的物件的適當地對齊物件的任何型別。  若要得到 `void` 之外的型別指標，請在傳回值上使用型別轉換。  
  
## 備註  
 `calloc` 函式會配置 `num` 項目的陣列 ，每個儲存空間 `size` 的長度 \(以位元組為單位\)。  每個元素初始化為 0。  
  
 如果記憶體配置失敗，或是要求的記憶體數量超過 `_HEAP_MAXREQ`，則 `calloc` 會將 `errno` 設定為 `ENOMEM`。  如需有關這個錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `calloc` 會呼叫 `malloc` 以使用 C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 函來設定新的處理常式模式。  新的處理常式模式表示，失敗時，`malloc` 是否要呼叫由 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 設定的新處理常式。  根據預設， `malloc` 不會在無法配置記憶體時呼叫新的處理常式。  您可以覆寫這個預設行為，因此，當 `calloc` 無法配置記憶體時，`malloc` 會以 `new` 運算子因相同原因失敗時所執行的相同方式，呼叫新處理常式。  若要覆寫預設值，請呼叫  
  
```  
_set_new_mode(1)  
```  
  
 及早在您的程式中呼叫，或與 NEWMODE.OBJ 連結 \(請參閱[連結選項](../../c-runtime-library/link-options.md)\)。  
  
 當應用程式使用 C 執行期程式庫偵錯版本連結時，`calloc` 會解析為 [\_calloc\_dbg](../../c-runtime-library/reference/calloc-dbg.md)。  如需堆積在偵錯過程中的運作，請參閱 [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md) 。  
  
 `calloc` 會標示 `__declspec(noalias)` 及 `__declspec(restrict)`，這表示函式保證不會修改全域變數且傳回的指標不會產生別名。  如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`calloc`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_calloc.c  
// This program uses calloc to allocate space for  
// 40 long integers. It initializes each element to zero.  
  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   long *buffer;  
  
   buffer = (long *)calloc( 40, sizeof( long ) );  
   if( buffer != NULL )  
      printf( "Allocated 40 long integers\n" );  
   else  
      printf( "Can't allocate memory\n" );  
   free( buffer );  
}  
```  
  
  **Allocated 40 long integers**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)