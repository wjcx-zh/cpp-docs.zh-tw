---
title: calloc
description: C 執行時間程式庫函數 calloc 會配置零初始化的記憶體。
ms.date: 09/27/2019
api_name:
- calloc
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: 228ec6d01a6f57ff98a9030f5a6d82e4c57388cd
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685370"
---
# <a name="calloc"></a>calloc

配置記憶體中項目初始化為 0 的陣列。

## <a name="syntax"></a>語法

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>參數

*number*<br/>
項目數。

*size*<br/>
每個項目的長度 (位元組)。

## <a name="return-value"></a>傳回值

**calloc**會傳回已配置空間的指標。 傳回值所指向的儲存空間一定可以適當地對齊任何物件類型之儲存區的保證。 若要取得**void**以外類型的指標，請在傳回值上使用類型轉換。

## <a name="remarks"></a>備註

**Calloc**函式會配置*數位*元素陣列的儲存空間，每個長度的*大小*為個位元組。 每個元素都會初始化為 0。

如果記憶體配置失敗，或所要求的記憶體數量超過 **_HEAP_MAXREQ**，則**calloc**會將**errno**設定為**ENOMEM** 。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

在 Microsoft 執行中，如果*數位*或*大小*為零，則**calloc**會傳回非零大小之配置區塊的指標。 嘗試透過傳回的指標來讀取或寫入會導致未定義的行為。

**calloc**會使用C++ [_set_new_mode](set-new-mode.md)函數來設定*新的處理常式模式*。 新的處理常式模式指出，在失敗時， **calloc**是否會呼叫[_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **calloc**不會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫此預設行為，如此一來，當**calloc**無法配置記憶體時，它會呼叫新的處理常式常式，就像**新**的運算子因為相同的原因而失敗時一樣。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

在您的程式初期，或與*newmode.obj 連結。OBJ* （請參閱[連結選項](../../c-runtime-library/link-options.md)）。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **calloc**會解析為[_calloc_dbg](calloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**calloc**標示為 `__declspec(noalias)`，`__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**calloc**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
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

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
