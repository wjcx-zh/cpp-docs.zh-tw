---
title: _aligned_msize_dbg
ms.date: 11/04/2016
apiname:
- _aligned_msize_dbg
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
- _aligned_msize_dbg
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
ms.openlocfilehash: 054f7b88f93eef37a9a88fbb7895452f7c158716
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342027"
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg

傳回堆積中所配置的記憶體區塊大小 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
size_t _aligned_msize_dbg(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
記憶體區塊的指標。

*alignment*<br/>
對齊值，必須是 2 的整數冪。

*offset*<br/>
記憶體配置中要強制對齊的位移。

## <a name="return-value"></a>傳回值

傳回不帶正負號的整數大小 (以位元組為單位)。

## <a name="remarks"></a>備註

*對齊*並*位移*值必須是傳遞至配置區塊函式的值相同。

**_aligned_msize_dbg**是偵錯版本[_aligned_msize](aligned-msize.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，每次呼叫 **_aligned_msize_dbg**的呼叫會降低 **_aligned_msize**。 兩者 **_aligned_msize**並 **_aligned_msize_dbg**計算的基底堆積中的記憶體區塊大小，但 **_aligned_msize_dbg**將偵錯功能：它包含在傳回大小的記憶體區塊使用者部分任一端使用緩衝區。

這個函式會驗證其參數。 如果*memblock*為 null 指標或*對齊*不是 2 的乘冪 **_msize**叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md). 如果已處理的錯誤，則函式會設定**errno**要**EINVAL**並傳回-1。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_msize_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
