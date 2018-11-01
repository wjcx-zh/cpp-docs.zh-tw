---
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 481109a5ed7d137aa2d10c77955a2f460cba43c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507532"
---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg

在指定的對齊界限上配置記憶體 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*size*<br/>
要求的記憶體配置的大小。

*對齊方式*<br/>
對齊值，必須是 2 的整數冪。

*offset*<br/>
記憶體配置中要強制對齊的位移。

*filename*<br/>
要求配置作業之原始程式檔名稱的指標或**NULL**。

*linenumber*<br/>
其中要求配置作業，原始程式檔中的行號或**NULL**。

## <a name="return-value"></a>傳回值

已配置的記憶體區塊的指標或**NULL**如果作業失敗。

## <a name="remarks"></a>備註

**_aligned_offset_malloc_dbg**是偵錯版本[_aligned_offset_malloc](aligned-offset-malloc.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，每次呼叫 **_aligned_offset_malloc_dbg**的呼叫會降低 **_aligned_offset_malloc**。 兩者 **_aligned_offset_malloc**並 **_aligned_offset_malloc_dbg**配置基底堆積中中的記憶體區塊，但 **_aligned_offset_malloc_dbg**提供數個偵錯功能： 以測試遺漏，來追蹤特定配置類型的區塊類型參數的區塊使用者部分任一端使用緩衝區和*檔名*/*linenumber*來判斷配置要求來源的資訊。

**_aligned_offset_malloc_dbg**配置記憶體區塊，使用比要求稍微多一些的空間*大小*。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。

**_aligned_offset_malloc_dbg**巢狀元素; 需要對齊的情況很有用，例如，如果巢狀類別需要對齊時。

**_aligned_offset_malloc_dbg**為基礎**malloc**; 如需詳細資訊，請參閱[malloc](malloc.md)。

此函式會將**errno**要**ENOMEM**如果記憶體配置失敗，或者要求的大小大於 **_HEAP_MAXREQ**。 如需詳細資訊**errno**，請參閱[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_malloc**會驗證其參數。 如果*對齊*不是 2 的冪，或如果*位移*大於或等於*大小*和非零值，這個函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則此函數會傳回**NULL**並設定**errno**來**EINVAL**。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如需配置區塊類型和其使用方式的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
