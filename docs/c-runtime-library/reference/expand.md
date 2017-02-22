---
title: "_expand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_expand"
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
  - "_bexpand"
  - "fexpand"
  - "expand"
  - "nexpand"
  - "_fexpand"
  - "_nexpand"
  - "bexpand"
  - "_expand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_expand 函式"
  - "expand 函式"
  - "記憶體區塊, 變更大小"
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _expand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變更記憶體區塊的大小。  
  
## 語法  
  
```  
void *_expand(   
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
 `_expand` 傳回 Void 指標到重新配置的記憶體區塊。  `_expand`不同於 `realloc`，無法捲動區塊變更其大小。  因此，如果有充足的記憶體以展開區塊，而不需不移動它，則給 `_expand` 的 `memblock` 參數與傳回值具有相同值。  
  
 發生在它的作業偵測到錯誤時，`_expand` 傳回 `NULL` 。  例如，如果已將 `_expand` 設定用來壓縮記憶體區塊，它可能會偵測小區塊堆積或無效的區塊指標並傳回 `NULL`。  
  
 如果沒有足夠的記憶體以展開區塊以供特定大小且不移動它，則函式會傳回 `NULL`。  `_expand` 不會回傳小於大小要求的區塊擴展。  如果失敗， `errno` 表示錯誤的性質。  如需 `errno` 的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 傳回值指向保證可以儲存任何型別的物件的適當地對齊的儲存空間。  若要檢查項目的新大小，請使用 `_msize`。  若要得到 `void` 之外的型別指標，請在傳回值上使用型別轉換。  
  
## 備註  
 `_expand` 函式變更先前配置的記憶體區塊的大小會嘗試展開或壓縮區塊，而不會移動它的堆積的位置。  對區塊的 `memblock` 參數中開始點。  `size` 參數給區塊以位元組為單位的新大小。  區塊的內容不會由新舊大小決定變更。  `memblock` 不能是已經釋放的區塊。  
  
> [!NOTE]
>  在 64 位元平台上，因此，如果新的大小小於目前的大小， `_expand` 可能不會縮小成區塊；特別是，如果是因為區塊大小小於 16K 因此配置低分散堆積，則 `_expand` 留下區塊未變更並傳回 `memblock`。  
  
 當應用程式使用 C 執行期程式庫偵錯版本連結時，`_expand` 會解析為 [\_expand\_dbg](../../c-runtime-library/reference/expand-dbg.md)。  如需堆積在偵錯過程中的運作，請參閱 [The CRT Debug Heap](../Topic/CRT%20Debug%20Heap%20Details.md) 。  
  
 這個函式會驗證它的參數。  如果 `memblock`為 null 指標，則函式叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `NULL`。  如果 `size` 大於 `_HEAP_MAXREQ`， `errno` 設定為 `ENOMEM` ，而且函式會傳回 `NULL`。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_expand`|\<malloc.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_expand.c  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char *bufchar;  
   printf( "Allocate a 512 element buffer\n" );  
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )  
      exit( 1 );  
   printf( "Allocated %d bytes at %Fp\n",   
         _msize( bufchar ), (void *)bufchar );  
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )  
      printf( "Can't expand" );  
   else  
      printf( "Expanded block to %d bytes at %Fp\n",   
            _msize( bufchar ), (void *)bufchar );  
   // Free memory   
   free( bufchar );  
   exit( 0 );  
}  
```  
  
  **配置 512 個元素緩衝區**  
**在002C12BC配置 512 個位元組**  
**在 002C12BC為 1024 個位元組的展開區塊**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_msize](../../c-runtime-library/reference/msize.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)