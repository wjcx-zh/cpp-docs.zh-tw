---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: 3db61d494ea94c9ccbf2844c9f47df66dad87ff7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939889"
---
# <a name="_aligned_malloc_dbg"></a>_aligned_malloc_dbg

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

*alignment*<br/>
對齊值，必須是 2 的整數冪。

*filename*<br/>
要求配置作業之原始程式檔的名稱的指標，或為 NULL。

*linenumber*<br/>
原始程式檔中的行號，其中要求配置作業，或為 NULL。

## <a name="return-value"></a>傳回值

已配置之記憶體區塊的指標，如果作業失敗，則為 Null。

## <a name="remarks"></a>備註

**_aligned_malloc_dbg**是[_aligned_malloc](aligned-malloc.md)函數的調試版本。 未定義[_debug](../../c-runtime-library/debug.md)時，會將 **_aligned_malloc_dbg**的每個呼叫縮減為`_aligned_malloc`的呼叫。 和`_aligned_malloc` **_aligned_malloc_dbg**都會配置基底堆積中的記憶體區塊，但 **_aligned_malloc_dbg**提供數個偵錯工具功能：在區塊的使用者部分的任一端使用緩衝區以測試遺漏，以及*filename*linenumber 資訊以判斷配置要求的來源。 / 使用區塊類型參數追蹤特定的配置類型，並不是針對對齊配置所支援的偵錯工具功能。 對齊的配置會顯示為 _NORMAL_BLOCK 區塊類型。

**_aligned_malloc_dbg**會以比所要求*大小*稍微多一點的空間來配置記憶體區塊。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。

如果記憶體`errno`配置`ENOMEM`失敗，或所需的記憶體數量（包括先前所述的額外負荷）超過`_HEAP_MAXREQ`，則 **_aligned_malloc_dbg**會將設為。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_malloc_dbg**會驗證其參數。 如果*對齊*不是2的乘冪，或*大小*為零，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回 Null，並`errno`將`EINVAL`設為。

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