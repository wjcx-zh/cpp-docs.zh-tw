---
title: _aligned_malloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 076ccfcf164eb17e2a855f175c8714cd63a91817
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093038"
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg

使用額外空間為偵錯標頭及覆寫緩衝區，依指定的對齊界限配置記憶體 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*size*<br/>
要求的記憶體配置大小。

*對齊方式*<br/>
對齊值，必須是 2 的整數冪。

*filename*<br/>
要求配置作業之原始程式檔的名稱的指標，或為 NULL。

*linenumber*<br/>
原始程式檔中的行號，其中要求配置作業，或為 NULL。

## <a name="return-value"></a>傳回值

已配置之記憶體區塊的指標或如果作業失敗，則為 NULL。

## <a name="remarks"></a>備註

**_aligned_malloc_dbg**是偵錯版本[_aligned_malloc](aligned-malloc.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，每次呼叫 **_aligned_malloc_dbg**的呼叫會降低`_aligned_malloc`。 兩者`_aligned_malloc`並 **_aligned_malloc_dbg**配置基底堆積中中的記憶體區塊，但 **_aligned_malloc_dbg**提供數個偵錯功能： 使用者部分的任一端使用緩衝區區塊以測試遺漏，以及*檔名*/*linenumber*判斷配置要求來源的資訊。

**_aligned_malloc_dbg**配置記憶體區塊，使用比要求稍微多一些的空間*大小*。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。

**_aligned_malloc_dbg**設定`errno`要`ENOMEM`若記憶體配置失敗或需要的記憶體數量 （包含先前所述的額外負荷） 超過`_HEAP_MAXREQ`。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_malloc_dbg**會驗證其參數。 如果*對齊*不是 2 的冪，或*大小*為零，此函式會叫用無效參數處理常式中，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 若要繼續，此函數會傳回 NULL 和集合允許執行`errno`至`EINVAL`。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)