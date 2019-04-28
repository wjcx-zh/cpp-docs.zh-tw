---
title: calloc
ms.date: 11/04/2016
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
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: 59aa535136cf32ea5dd68b8917ec969eee41e2ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347726"
---
# <a name="calloc"></a>calloc

配置記憶體中項目初始化為 0 的陣列。

## <a name="syntax"></a>語法

```C
void *calloc(
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>參數

*number*<br/>
項目數。

*size*<br/>
每個項目的長度 (位元組)。

## <a name="return-value"></a>傳回值

**calloc**傳回指標至配置的空間。 傳回值所指向的儲存空間一定可以適當地對齊任何物件類型之儲存區的保證。 若要取得的指標類型以外的其他**void**，使用類型轉換的傳回值。

## <a name="remarks"></a>備註

**Calloc**函式會配置儲存空間的陣列*數目*項目，而且每個長度*大小*位元組。 每個元素都會初始化為 0。

**calloc**設定**errno**要**ENOMEM**如果記憶體配置失敗，或所要求的記憶體數量超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**calloc**呼叫**malloc**使用C++ [_set_new_mode](set-new-mode.md)函式來設定新的處理常式模式。 新的處理常式模式會指出是否在失敗時， **malloc**就是呼叫所設定的新處理常式[_set_new_handler](set-new-handler.md)。 根據預設， **malloc**不會呼叫新的處理常式無法配置記憶體。 您可以覆寫此預設行為，讓，當**calloc**無法配置記憶體， **malloc**呼叫新的處理常式在相同方式來**新**運算子因當它失敗，相同的原因。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

，或使用 NEWMODE.OBJ 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

當偵錯版本的 C 執行階段程式庫，連結的應用程式時**calloc**解析[_calloc_dbg](calloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**calloc**標示`__declspec(noalias)`和`__declspec(restrict)`，這表示保證函式不能修改全域變數，並傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

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
