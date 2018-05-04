---
title: _msize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _msize
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
- msize
- _msize
dev_langs:
- C++
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9e27751072891bcabc0b068cb5ca57b571d35d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="msize"></a>_msize

傳回堆積中所配置的記憶體區塊大小。

## <a name="syntax"></a>語法

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
記憶體區塊的指標。

## <a name="return-value"></a>傳回值

**_msize**傳回做為不帶正負號整數的大小 （以位元組為單位）。

## <a name="remarks"></a>備註

**_Msize**函式傳回的大小，以位元組為單位的呼叫所配置的記憶體區塊**calloc**， **malloc**，或**realloc**。

當應用程式的 C 執行階段程式庫的偵錯版本連結時 **_msize**解析成[_msize_dbg](msize-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

這個函式會驗證其參數。 如果*memblock*為 null 指標， **_msize**叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 處理錯誤，函式會將**errno**至**EINVAL**並傳回-1。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

請參閱 [realloc](realloc.md) 的範例。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
