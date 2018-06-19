---
title: calloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6986e1caec25cd544919039f690544af429524af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394882"
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

*數字*<br/>
項目數。

*size*<br/>
每個項目的長度 (位元組)。

## <a name="return-value"></a>傳回值

**calloc**讓指標回到配置的空間。 傳回值所指向的儲存空間一定可以適當地對齊任何物件類型之儲存區的保證。 若要取得指標的類型以外**void**，使用類型，對傳回值轉型。

## <a name="remarks"></a>備註

**Calloc**函式會配置儲存空間陣列的*數目*項目，每個長度*大小*位元組。 每個元素都會初始化為 0。

**calloc**設定**errno**至**ENOMEM**記憶體配置失敗，或要求的記憶體數量超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**calloc**呼叫**malloc**使用 c + + [_set_new_mode](set-new-mode.md)函式可設定新的處理常式模式。 新的處理常式模式指出是否在失敗時， **malloc**是新的處理常式呼叫所設定的[_set_new_handler](set-new-handler.md)。 根據預設， **malloc**不會呼叫新的處理常式在無法配置記憶體。 您可以覆寫此預設行為，讓，當**calloc**無法配置記憶體， **malloc**呼叫新的處理常式在相同的方式來**新**運算子會當它失敗基於相同原因。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

，或使用 NEWMODE.OBJ 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

當應用程式的 C 執行階段程式庫的偵錯版本連結時**calloc**解析成[_calloc_dbg](calloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**calloc**標示`__declspec(noalias)`和`__declspec(restrict)`，也就是說，不保證函式修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
