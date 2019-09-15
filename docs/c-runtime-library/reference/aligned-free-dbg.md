---
title: _aligned_free_dbg
ms.date: 11/04/2016
api_name:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: b510d16b6e784202094bb05e6364f7af1b1fff97
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939911"
---
# <a name="_aligned_free_dbg"></a>_aligned_free_dbg

釋放使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 所配置的記憶體區塊 (僅限偵錯)。

## <a name="syntax"></a>語法

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
傳回至[_aligned_malloc](aligned-malloc.md)或[_aligned_offset_malloc](aligned-offset-malloc.md)函式之記憶體區塊的指標。

## <a name="remarks"></a>備註

**_Aligned_free_dbg**函數是[_aligned_free](aligned-free.md)函數的 debug 版本。 未定義[_debug](../../c-runtime-library/debug.md)時，會將 **_aligned_free_dbg**的每個呼叫縮減為`_aligned_free`的呼叫。 和`_aligned_free` **_aligned_free_dbg**都會釋放基底堆積中的記憶體區塊，但 **_aligned_free_dbg**會包含偵錯工具功能：將釋放的區塊保留在堆積的連結清單中，以模擬記憶體不足的狀況。

在執行免費作業之前， **_aligned_free_dbg**會對所有指定的檔案和區塊位置執行有效性檢查。 應用程式不需要提供此資訊。 釋放記憶體區塊時，偵錯堆積管理員會自動檢查使用者部分每一端的緩衝區完整性，並在發生覆寫時發出錯誤報表。 如果已設定[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標的 _CRTDBG_DELAY_FREE_MEM_DF 位欄位，釋放的區塊會填入值0xDD、指派 _FREE_BLOCK 區塊類型，並保留在堆積的記憶體區塊連結清單中。

若釋放記憶體發生錯誤，會使用來自作業系統且具有失敗性質的資訊設定 `errno`。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)