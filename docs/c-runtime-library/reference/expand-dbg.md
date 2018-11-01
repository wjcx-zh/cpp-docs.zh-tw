---
title: _expand_dbg
ms.date: 11/04/2016
apiname:
- _expand_dbg
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
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: cc3aa2b7e39b52eb71ac10a9b5c4a221ba6fb70c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663797"
---
# <a name="expanddbg"></a>_expand_dbg

以展開或收縮區塊的方式調整堆積中的指定記憶體區塊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void *_expand_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*保留使用者資料*<br/>
之前配置的記憶體區塊的指標。

*newSize*<br/>
要求的新區塊大小 (以位元組為單位)。

*blockType*<br/>
已調整大小的區塊的要求類型： **_CLIENT_BLOCK**或是 **_NORMAL_BLOCK**。

*filename*<br/>
要求的原始程式檔的名稱指標展開作業或**NULL**。

*linenumber*<br/>
要求展開作業所在的原始程式檔中的行號或**NULL**。

*檔名*並*linenumber*參數時，就只能使用 **_expand_dbg**已明確呼叫或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定義前置處理器常數。

## <a name="return-value"></a>傳回值

成功完成時， **_expand_dbg**傳回的已調整大小的記憶體區塊的指標。 因為記憶體未移動，所以位址和 userData 相同。 如果發生錯誤，或區塊無法展開至要求的大小，它會傳回**NULL**。 如果發生失敗， **errno**與作業系統本質的資訊失敗。 如需詳細資訊**errno**，請參閱[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Expand_dbg**函式是偵錯版本的 _[展開](expand.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，每次呼叫 **_expand_dbg**的呼叫會降低 **_expand**。 兩者 **_expand**並 **_expand_dbg**調整基底堆積中的記憶體區塊的大小，但 **_expand_dbg**容納數種偵錯功能： 使用者的任一端使用緩衝區一部分的區塊，以測試遺漏，來追蹤特定配置類型的區塊類型參數和*檔名*/*linenumber*資訊來判斷的原點配置要求。

**_expand_dbg**調整大小稍微多一些的空間比要求與指定的記憶體區塊*newSize*。 *newSize*可能大於或小於原本配置的記憶體區塊的大小。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 展開或收縮原始記憶體區塊即可調整大小。 **_expand_dbg**不會移動記憶體區塊，如同[_realloc_dbg](realloc-dbg.md)函式。

當*newSize*大於原始區塊會展開記憶體區塊的大小。 在展開時，如果記憶體區塊無法展開以容納所要求的大小**NULL**會傳回。 當*newSize*少於原始區塊的記憶體區塊的大小簽約直到取得新的大小。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式與其偵錯版本間之差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

這個函式會驗證它的參數。 如果*memblock*為 null 指標，或如果大小大於 **_HEAP_MAXREQ**，此函式叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回**NULL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>註解

此程式的輸出取決於您的電腦能否展開所有區段。 如果所有區段都能展開，就會在 [輸出] 區段反映輸出。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
