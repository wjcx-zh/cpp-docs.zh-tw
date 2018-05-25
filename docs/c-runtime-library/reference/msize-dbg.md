---
title: _msize_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _msize_dbg
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
apitype: DLLExport
f1_keywords:
- _msize_dbg
- msize_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks
- _msize_dbg function
- msize_dbg function
ms.assetid: a333f4b6-f8a2-4e61-bb69-cb34063b8cef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80d3f3a7b2b0086df6cba9654dc4365697520776
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="msizedbg"></a>_msize_dbg

計算堆積中的記憶體區塊大小 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
size_t _msize_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>參數

*UserData*<br/>
要決定其大小之記憶體區塊的指標。

*blockType*<br/>
指定的記憶體區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

## <a name="return-value"></a>傳回值

成功完成， **_msize_dbg**傳回的大小 （以位元組為單位） 在指定的記憶體區塊; 否則它會傳回**NULL**。

## <a name="remarks"></a>備註

**_msize_dbg**是偵錯版本的 _[msize](msize.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，每次呼叫 **_msize_dbg**呼叫會降 **_msize**。 同時 **_msize**和 **_msize_dbg**計算基底堆積中的記憶體區塊的大小，但 **_msize_dbg**加入兩個偵錯功能： 它包含任一端使用緩衝區使用者的一部分傳回的大小和它的記憶體區塊可讓特定的區塊類型的大小計算。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

這個函式會驗證其參數。 如果*memblock*為 null 指標， **_msize**叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 處理錯誤，函式會將**errno**至**EINVAL**並傳回-1。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_msize_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_msize_dbg.c
// compile with: /MTd
/*
* This program allocates a block of memory using _malloc_dbg
* and then calls _msize_dbg to display the size of that block.
* Next, it uses _realloc_dbg to expand the amount of
* memory used by the buffer and then calls _msize_dbg again to
* display the new amount of memory allocated to the buffer.
*/

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
        long *buffer, *newbuffer;
        size_t size;

        /*
         * Call _malloc_dbg to include the filename and line number
         * of our allocation request in the header
         */
        buffer = (long *)_malloc_dbg( 40 * sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
        if( buffer == NULL )
               exit( 1 );

        /*
         * Get the size of the buffer by calling _msize_dbg
         */
        size = _msize_dbg( buffer, _NORMAL_BLOCK );
        printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

        /*
         * Reallocate the buffer using _realloc_dbg and show the new size
         */
        newbuffer = _realloc_dbg( buffer, size + (40 * sizeof(long)), _NORMAL_BLOCK, __FILE__, __LINE__ );
        if( newbuffer == NULL )
               exit( 1 );
        buffer = newbuffer;
        size = _msize_dbg( buffer, _NORMAL_BLOCK );
        printf( "Size of block after _realloc_dbg of 40 more longs: %u\n", size );

        free( buffer );
        exit( 0 );
}
```

### <a name="output"></a>輸出

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _realloc_dbg of 40 more longs: 320
```

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
