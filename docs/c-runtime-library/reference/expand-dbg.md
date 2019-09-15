---
title: _expand_dbg
ms.date: 11/04/2016
api_name:
- _expand_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: 836b9cffcf0367f248a14469b30c1a355e2bdec2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941583"
---
# <a name="_expand_dbg"></a>_expand_dbg

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

*userData*<br/>
之前配置的記憶體區塊的指標。

*newSize*<br/>
要求的新區塊大小 (以位元組為單位)。

*blockType*<br/>
已調整大小之區塊的要求類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
要求展開作業之原始程式檔的名稱的指標，或為**Null**。

*linenumber*<br/>
要求展開作業的原始程式檔中的行號，或**為 Null**。

只有在已明確呼叫 **_expand_dbg** ，或已定義[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)預處理器常數時，才可以使用*filename*和*linenumber*參數。

## <a name="return-value"></a>傳回值

成功完成時， **_expand_dbg**會傳回已調整大小之記憶體區塊的指標。 因為記憶體未移動，所以位址和 userData 相同。 如果發生錯誤或區塊無法展開為要求的大小，則會傳回**Null**。 如果發生失敗， **errno**會包含有關失敗本質的作業系統資訊。 如需**errno**的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Expand_dbg**函數是 _[expand](expand.md)函數的 debug 版本。 未定義[_debug](../../c-runtime-library/debug.md)時，每個 **_expand_dbg**的呼叫都會縮減為 **_expand**的呼叫。 **_Expand**和 **_expand_dbg**都會調整基底堆積中的記憶體區塊大小，但 **_expand_dbg**會容納數個偵錯工具：在區塊的使用者部分的任一端使用緩衝區以測試遺漏，以及要追蹤的區塊類型參數特定配置類型和*filename* / *linenumber*資訊，以判斷配置要求的來源。

**_expand_dbg**會以比所要求的*newSize*稍微多一點的空間，來調整指定的記憶體區塊大小。 *newSize*可能大於或小於原始配置的記憶體區塊大小。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 展開或收縮原始記憶體區塊即可調整大小。 **_expand_dbg**不會移動記憶體區塊，就像[_realloc_dbg](realloc-dbg.md)函數一樣。

當*newSize*大於原始區塊大小時，記憶體區塊會展開。 在展開期間，如果無法延伸記憶體區塊以容納所要求的大小，則會傳回**Null** 。 當*newSize*小於原始區塊大小時，記憶體區塊會被收縮，直到取得新的大小為止。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式與其偵錯版本間之差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

這個函式會驗證它的參數。 如果*memblock*為 null 指標，或大小大於 **_HEAP_MAXREQ**，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**Null**。

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
