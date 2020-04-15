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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 21ae07c90bbf9a729a212a97b7de3e0916f8e2c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350593"
---
# <a name="_aligned_msize"></a>_aligned_msize

傳回堆積中所配置的記憶體區塊大小。

## <a name="syntax"></a>語法

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
記憶體區塊的指標。

*對齊*<br/>
對齊值，必須是 2 的整數冪。

*位移*<br/>
記憶體配置中要強制對齊的位移。

## <a name="return-value"></a>傳回值

傳回不帶正負號的整數大小 (以位元組為單位)。

## <a name="remarks"></a>備註

**_aligned_msize**函數返回調用[_aligned_malloc](aligned-malloc.md)或[_aligned_realloc](aligned-realloc.md)分配的記憶體塊的大小(以位元組為單位)。 *對齊*值和*偏移*值必須與傳遞給分配塊的函數的值相同。

當應用程式連結到 C 執行時庫的除錯版本時 **,_aligned_msize**解析為[_aligned_msize_dbg](aligned-msize-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

這個函式會驗證其參數。 如果*memblock*是空指標,或者*對齊*不是 2 的電源 **,_msize**調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果處理了錯誤,函數將**errno**設置到**EINVAL**並返回 -1。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
