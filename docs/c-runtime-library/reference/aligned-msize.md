---
title: _aligned_msize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_msize
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _aligned_msize
- aligned_msize
dev_langs:
- C++
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2375ec8f61a95ec018ea55cc1f891ad8049748c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393101"
---
# <a name="alignedmsize"></a>_aligned_msize

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

*對齊方式*<br/>
對齊值，必須是 2 的整數冪。

*offset*<br/>
記憶體配置中要強制對齊的位移。

## <a name="return-value"></a>傳回值

傳回不帶正負號的整數大小 (以位元組為單位)。

## <a name="remarks"></a>備註

**_Aligned_msize**函式傳回的大小，以位元組為單位的呼叫所配置的記憶體區塊[_aligned_malloc](aligned-malloc.md)或[_aligned_realloc](aligned-realloc.md)。 *對齊*和*位移*值必須是傳遞至配置的區塊的函式的值相同。

當應用程式的 C 執行階段程式庫的偵錯版本連結時 **_aligned_msize**解析成[_aligned_msize_dbg](aligned-msize-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

這個函式會驗證其參數。 如果*memblock*為 null 指標或*對齊*不是 2 的乘冪， **_msize**叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md). 處理錯誤，函式會將**errno**至**EINVAL**並傳回-1。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
