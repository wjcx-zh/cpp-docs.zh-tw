---
title: _recalloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3de6adddc4e7d95f3212c80666816d4855897388
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451045"
---
# <a name="recallocdbg"></a>_recalloc_dbg

重新配置陣列，並將其項目初始化為 0 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*UserData*<br/>
之前配置的記憶體區塊的指標。

*數字*<br/>
要求的記憶體區塊數。

*size*<br/>
要求的每個記憶體區塊大小 (位元組)。

*blockType*<br/>
要求的記憶體區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

*filename*<br/>
要求配置作業之原始程式檔名稱的指標或**NULL**。

*linenumber*<br/>
要求配置作業，原始程式檔中的行號或**NULL**。

*Filename*和*linenumber*參數時，就只能使用 **_recalloc_dbg**明確呼叫或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定義前置處理器常數。

## <a name="return-value"></a>傳回值

成功完成時，此函式傳回重新配置的記憶體區塊的使用者部分的指標，呼叫新的處理常式函式，或是傳回**NULL**。 如需傳回行為的完整說明，請參閱下列＜備註＞一節。 如需如何使用新處理常式函式的詳細資訊，請參閱 [_recalloc](recalloc.md) 函式。

## <a name="remarks"></a>備註

**_recalloc_dbg**是偵錯版本的[_recalloc](recalloc.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，每次呼叫 **_recalloc_dbg**呼叫會降 **_recalloc**。 同時 **_recalloc**和 **_recalloc_dbg**重新配置基底堆積中的記憶體區塊，但 **_recalloc_dbg**容納數種偵錯功能： 任一端使用緩衝區以測試遺漏的區塊的使用者部分的區塊型別參數，來追蹤特定配置類型和*filename*/*linenumber*資訊來判斷配置要求來源。

**_recalloc_dbg**重新配置指定的記憶體區塊，以稍微多一些的空間比要求的大小 (*數目* * *大小*) 可以是大於或小於的大小原始配置的記憶體區塊。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 重新配置可能會導致將原始記憶體區塊移到堆積中的不同位置，也可能會變更記憶體區塊的大小。 區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。

**_recalloc_dbg**設定**errno**至**ENOMEM**記憶體配置失敗。**EINVAL**傳回如果需要的記憶體數量 （包含之前提到的額外負荷） 超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
