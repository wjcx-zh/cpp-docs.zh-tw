---
title: _malloc_dbg
ms.date: 11/04/2016
apiname:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
ms.openlocfilehash: 64fb40028d9130278077f3d05dd1e25914dba212
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156937"
---
# <a name="mallocdbg"></a>_malloc_dbg

使用額外空間為偵錯標頭及覆寫緩衝區配置堆積中的記憶體區塊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*size*<br/>
要求的記憶體區塊大小 (位元組)。

*blockType*<br/>
要求的記憶體區塊類型： **_CLIENT_BLOCK**或是 **_NORMAL_BLOCK**。

*filename*<br/>
要求配置作業之原始程式檔名稱的指標或**NULL**。

*linenumber*<br/>
其中要求配置作業，原始程式檔中的行號或**NULL**。

*檔名*並*linenumber*參數時，就只能使用 **_malloc_dbg**已明確呼叫或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定義前置處理器常數。

## <a name="return-value"></a>傳回值

成功完成時，此函式會傳回配置的記憶體區塊使用者部分的指標，呼叫新的處理常式函式，或傳回**NULL**。 如需傳回行為的完整說明，請參閱下列＜備註＞一節。 如需如何使用新的處理函式的詳細資訊，請參閱 [malloc](malloc.md) 函式。

## <a name="remarks"></a>備註

**_malloc_dbg**是偵錯版本[malloc](malloc.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，每次呼叫 **_malloc_dbg**的呼叫會降低**malloc**。 兩者**malloc**並 **_malloc_dbg**配置基底堆積中中的記憶體區塊，但 **_malloc_dbg**提供數個偵錯功能： 使用者的任一端使用緩衝區一部分的區塊，以測試遺漏，來追蹤特定配置類型的區塊類型參數和*檔名*/*linenumber*資訊來判斷的原點配置要求。

**_malloc_dbg**配置記憶體區塊，使用比要求稍微多一些的空間*大小*。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。

**_malloc_dbg**設定**errno**要**ENOMEM**若記憶體配置失敗或需要的記憶體數量 （包含先前所述的額外負荷） 超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需如何使用的範例 **_malloc_dbg**，請參閱[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
