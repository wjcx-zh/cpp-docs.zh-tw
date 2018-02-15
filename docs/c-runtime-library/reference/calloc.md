---
title: calloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- calloc
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
- calloc
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f106ec1cd879282d557c492e4f19cdd01480575
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="calloc"></a>calloc
配置記憶體中項目初始化為 0 的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
void *calloc(   
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>參數  
 `num`  
 項目數。  
  
 `size`  
 每個項目的長度 (位元組)。  
  
## <a name="return-value"></a>傳回值  
 `calloc` 傳回所配置空間的指標。 傳回值所指向的儲存空間一定可以適當地對齊任何物件類型之儲存區的保證。 若要取得 `void` 以外之類型的指標，請對傳回值使用類型轉換。  
  
## <a name="remarks"></a>備註  
 `calloc` 函式會配置 `num` 項目陣列的儲存空間，而且每個長度都是 `size` 個位元組。 每個項目都會初始化為 0。  
  
 如果記憶體配置失敗，或所要求的記憶體數量超過 `_HEAP_MAXREQ`，`calloc` 會將 `errno` 設為 `ENOMEM`。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `calloc` 會呼叫 `malloc` 使用 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函式來設定新的處理常式模式。 此新的處理常式模式會指出失敗時，`malloc` 是否會呼叫 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 所設定的新處理常式。 根據預設，`malloc` 不會在失敗時呼叫新的處理常式來配置記憶體。 您可以覆寫這個預設行為，因此，在 `calloc` 無法配置記憶體時，`malloc` 會呼叫新的處理常式，其方法與 `new` 運算子因相同原因而失敗時所執行的方法相同。 若要覆寫預設值，請及早在程式中呼叫  
  
```  
_set_new_mode(1)  
```  
  
 ，或使用 NEWMODE.OBJ 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。  
  
 當應用程式與偵錯版本的 C 執行階段程式庫相連結時，`calloc` 會解析為 [_calloc_dbg](../../c-runtime-library/reference/calloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `calloc` 標記為 `__declspec(noalias)` 和 `__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`calloc`|\<stdlib.h> 和 \<malloc.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
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
  
```Output  
Allocated 40 long integers  
```  
  
## <a name="see-also"></a>請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)