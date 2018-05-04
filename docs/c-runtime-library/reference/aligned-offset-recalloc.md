---
title: _aligned_offset_recalloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_offset_recalloc
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
- aligned_offset_recalloc
- _aligned_offset_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9297defc32966209dd484da80e9230d6df5dbab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="alignedoffsetrecalloc"></a>_aligned_offset_recalloc

變更使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0。

## <a name="syntax"></a>語法

```C
void * _aligned_offset_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
目前記憶體區塊指標。

*數字*<br/>
項目數。

*size*<br/>
每個項目的長度 (位元組)。

*對齊方式*<br/>
對齊值，必須是 2 的整數冪。

*offset*<br/>
記憶體配置中要強制對齊的位移。

## <a name="return-value"></a>傳回值

**_aligned_offset_recalloc**傳回重新配置後 （且可能有移動） 記憶體區塊的 void 指標。 傳回值是**NULL**如果大小為零，且緩衝區引數不是**NULL**，或如果沒有足夠的可用記憶體將區塊展開為指定大小。 在第一種情況中，會釋放原始區塊。 在第二種情況中，原始區塊會保留不變。 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。

**_aligned_offset_recalloc**標示`__declspec(noalias)`和`__declspec(restrict)`，這表示，此函式保證不會修改全域變數和別名不是傳回的指標。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

## <a name="remarks"></a>備註

像[_aligned_offset_malloc](aligned-offset-malloc.md)， **_aligned_offset_recalloc**可讓結構對齊結構中的位移。

**_aligned_offset_recalloc**根據**malloc**。 如需有關使用 **_aligned_offset_malloc**，請參閱[malloc](malloc.md)。 如果*memblock*是**NULL**，函式呼叫 **_aligned_offset_malloc**內部。

此函式會將**errno**至**ENOMEM**若記憶體配置失敗，或是要求的大小 (*數目* * *大小*) 大於 **_HEAP_MAXREQ**。 如需有關**errno**，請參閱[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_recalloc**會驗證其參數。 如果*對齊*不是 2 的乘冪或*位移*大於或等於要求的大小，且為非零，此函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則此函數會傳回**NULL**並設定**errno**至**EINVAL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc.h>|

## <a name="see-also"></a>另請參閱

[資料對齊](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
