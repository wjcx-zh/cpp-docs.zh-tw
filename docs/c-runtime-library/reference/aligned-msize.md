---
title: _aligned_msize
ms.date: 4/2/2020
api_name:
- _aligned_msize
- _o__aligned_msize
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: 1037c63af17a844959bc72e42da2c33267b43004
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414031"
---
# <a name="_aligned_msize"></a>_aligned_msize

傳回堆積中所配置的記憶體區塊大小。

## <a name="syntax"></a>語法

```C
size_t _aligned_msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
記憶體區塊的指標。

*對準*<br/>
對齊值，必須是 2 的整數冪。

*offset*<br/>
記憶體配置中要強制對齊的位移。

## <a name="return-value"></a>傳回值

傳回不帶正負號的整數大小 (以位元組為單位)。

## <a name="remarks"></a>備註

**_Aligned_msize**函式會傳回[_aligned_malloc](aligned-malloc.md)或[_aligned_realloc](aligned-realloc.md)的呼叫所配置的記憶體區塊大小（以位元組為單位）。 *對齊*和*位移*值必須和傳遞給配置區塊的函式的值相同。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **_aligned_msize** 會解析為 [_aligned_msize_dbg](aligned-msize-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

這個函式會驗證其參數。 如果 *memblock* 為 null 指標或 *對齊* 不是2的乘冪， **_aligned_msize** 會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果已處理錯誤，函數會將 **errno** 設定為 **EINVAL** ，並傳回-1。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_msize**|\<malloc.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
