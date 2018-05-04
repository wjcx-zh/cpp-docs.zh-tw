---
title: _expand_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 023bda761454a6a1e18ce68c8e7576af2759abbf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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

*UserData*<br/>
之前配置的記憶體區塊的指標。

*newSize*<br/>
要求的新區塊大小 (以位元組為單位)。

*blockType*<br/>
要求的調整大小的區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
要求的原始程式檔的名稱指標展開作業或**NULL**。

*linenumber*<br/>
傳回展開作業的來源檔案中的行號或**NULL**。

*Filename*和*linenumber*參數時，就只能使用 **_expand_dbg**明確呼叫或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定義前置處理器常數。

## <a name="return-value"></a>傳回值

成功完成， **_expand_dbg**傳回調整大小的記憶體區塊的指標。 因為記憶體未移動，所以位址和 userData 相同。 如果發生錯誤，或為要求的大小，無法展開此區塊，它會傳回**NULL**。 如果發生失敗， **errno**與作業系統性質的資訊失敗。 如需有關**errno**，請參閱[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Expand_dbg**函式是偵錯版本的 _[展開](expand.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，每次呼叫 **_expand_dbg**呼叫會降 **_expand**。 同時 **_expand**和 **_expand_dbg**調整大小的記憶體區塊，在基底堆積中，但 **_expand_dbg**容納數種偵錯功能： 使用者的任一端使用緩衝區一部分的區塊，以測試遺漏，來追蹤特定配置類型的區塊型別參數和*filename*/*linenumber*來判斷來源的資訊配置要求。

**_expand_dbg**調整大小比要求稍微多一些的空間之指定的記憶體區塊*newSize*。 *newSize*可能會大於或小於原始配置的記憶體區塊的大小。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 展開或收縮原始記憶體區塊即可調整大小。 **_expand_dbg**不會移動的記憶體區塊，如同[_realloc_dbg](realloc-dbg.md)函式。

當*newSize*大於原始區塊的記憶體區塊的大小，就會展開。 記憶體區塊不能展開以容納所要求的大小，如果展開期間**NULL**傳回。 當*newSize*少於原始區塊的記憶體區塊的大小會收縮取得新的大小之前。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式與其偵錯版本間之差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

這個函式會驗證它的參數。 如果*memblock*為 null 指標，或大小是否大於 **_HEAP_MAXREQ**，此函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式**NULL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
