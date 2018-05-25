---
title: _realloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c4bb3eab58807805ec3c4fbc35611d268bbeee9
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="reallocdbg"></a>_realloc_dbg

以移動及/或調整區塊大小的方式重新配置堆積中的指定記憶體區塊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void *_realloc_dbg(
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
重新配置區塊的要求大小 (位元組)。

*blockType*<br/>
要求的重新配置區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
要求的原始程式檔的名稱指標**realloc**作業或**NULL**。

*linenumber*<br/>
原始程式檔中的行號其中**realloc**要求作業，或**NULL**。

*Filename*和*linenumber*參數時，就只能使用 **_realloc_dbg**明確呼叫或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定義前置處理器常數。

## <a name="return-value"></a>傳回值

成功完成時，此函式傳回重新配置的記憶體區塊的使用者部分的指標，呼叫新的處理常式函式，或是傳回**NULL**。 如需傳回行為的完整說明，請參閱下列＜備註＞一節。 如需如何使用新處理常式函式的詳細資訊，請參閱 [realloc](realloc.md) 函式。

## <a name="remarks"></a>備註

**_realloc_dbg**是偵錯版本的[realloc](realloc.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，每次呼叫 **_realloc_dbg**呼叫會降**realloc**。 同時**realloc**和 **_realloc_dbg**重新配置基底堆積中的記憶體區塊，但 **_realloc_dbg**容納數種偵錯功能： 的任一端使用緩衝區區塊以測試遺漏，來追蹤特定配置類型的區塊類型參數的使用者部分和*filename*/*linenumber*來判斷來源的資訊配置要求。

**_realloc_dbg**重新配置指定的記憶體區塊，使用比要求稍微多一些的空間*newSize*。 *newSize*可能會大於或小於原始配置的記憶體區塊的大小。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 重新配置可能會導致將原始記憶體區塊移到堆積中的不同位置，也可能會變更記憶體區塊的大小。 若記憶體區塊已移動，則會覆寫原始區塊的內容。

**_realloc_dbg**設定**errno**至**ENOMEM**若記憶體配置失敗或需要的記憶體數量 （包含之前提到的額外負荷） 超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

請參閱 [_msize_dbg](msize-dbg.md) 主題中的範例。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
