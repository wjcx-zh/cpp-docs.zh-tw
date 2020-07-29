---
title: calloc
description: C 執行時間程式庫函數 calloc 會配置零初始化的記憶體。
ms.date: 4/2/2020
api_name:
- calloc
- _o_calloc
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 067ce6f347f4b24ad8c85990e70fe4d79305535c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213628"
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

**calloc**會傳回已配置空間的指標。 傳回值所指向的儲存空間一定可以適當地對齊任何物件類型之儲存區的保證。 若要取得以外類型的指標 **`void`** ，請對傳回值使用類型轉換。

## <a name="remarks"></a>備註

**Calloc**函式會配置*數位*元素陣列的儲存空間，每個長度的*大小*為個位元組。 每個項目都會初始化為 0。

如果記憶體配置失敗，或所要求的記憶體數量超過 **_HEAP_MAXREQ**，則**calloc**會將**errno**設定為**ENOMEM** 。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

在 Microsoft 執行中，如果*數位*或*大小*為零，則**calloc**會傳回非零大小之配置區塊的指標。 嘗試透過傳回的指標來讀取或寫入會導致未定義的行為。

**calloc**會使用 c + + [_set_new_mode](set-new-mode.md)函數來設定*新的處理常式模式*。 新的處理常式模式指出，在失敗時， **calloc**是否會呼叫[_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **calloc**不會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫此預設行為，如此一來，當**calloc**無法配置記憶體時，它會呼叫新的處理常式常式，其方式與 **`new`** 運算子因相同原因而失敗時所執行的相同。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

在您的程式初期，或與*newmode.obj 連結。OBJ* （請參閱[連結選項](../../c-runtime-library/link-options.md)）。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **calloc**會解析為[_calloc_dbg](calloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**calloc**標示為 `__declspec(noalias)` 和 `__declspec(restrict)` ，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
[受](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
