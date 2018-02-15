---
title: _expand | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _expand
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6b2bf8ba3e30165f11e3392e04519a3d49cfd4a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="expand"></a>_expand
變更記憶體區塊的大小。  
  
## <a name="syntax"></a>語法  
  
```  
void *_expand(   
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>參數  
 `memblock`  
 先前配置之記憶體區塊的指標。  
  
 `size`  
 新的大小 (以位元組計)。  
  
## <a name="return-value"></a>傳回值  
 `_expand` 會傳回重新配置記憶體區塊的 void 指標。 與 `realloc` 不同，`_expand` 無法移動區塊來變更其大小。 因此，如有足夠的可用記憶體能將區塊展開卻不必移動它，`_expand` 的 `memblock` 參數就和傳回的值相同。  
  
 在其作業期間偵測到錯誤時，`_expand` 會傳回 `NULL`。 例如，如果 `_expand` 是用來收縮記憶體區塊，它可能會偵測到小型區塊堆積的損毀，或無效的區塊指標，並傳回 `NULL`。  
  
 如果沒有足夠的可用記憶體將區塊展開至指定的大小卻不移動它，則此函式會傳回 `NULL`。 `_expand` 絕不會傳回大小小於要求的展開區塊。 如果失敗，`errno` 會指出失敗類別。 如需 `errno` 的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要檢查項目的新大小，請使用 `_msize`。 若要取得 `void` 以外之類型的指標，請對傳回值使用類型轉換。  
  
## <a name="remarks"></a>備註  
 `_expand` 函式會嘗試展開或收縮區塊，變更先前配置的記憶體區塊大小，不用移動自己在堆積中的位置。 `memblock` 參數會指向區塊的開頭。 `size` 參數會指定區塊的新大小，以位元組為單位。 區塊內容在不超過新的和舊的大小範圍內不會變更。 `memblock` 不該是釋出的區塊。  
  
> [!NOTE]
>  在 64 位元的平台中，如果新的大小小於目前的大小，`_expand` 可能不收縮區塊；但若因為區塊的大小小於 16 K，而配置在低分散堆積中，`_expand` 就不會變更區塊，並傳回 `memblock`。  
  
 當應用程式與偵錯版本的 C 執行階段程式庫相連結時，`_expand` 會解析為 [_expand_dbg](../../c-runtime-library/reference/expand-dbg.md)。 如需在偵錯程序期間如何管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。  
  
 這個函式會驗證它的參數。 如果 `memblock` 為 Null 指標，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行， `errno` 會設為 `EINVAL` ，且此函式會傳回 `NULL`。 如果 `size` 大於 `_HEAP_MAXREQ`，`errno` 會設為 `ENOMEM` 且函式會傳回 `NULL`。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_expand`|\<malloc.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
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
  
```Output  
Allocate a 512 element buffer  
Allocated 512 bytes at 002C12BC  
Expanded block to 1024 bytes at 002C12BC  
```  
  
## <a name="see-also"></a>請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_msize](../../c-runtime-library/reference/msize.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)