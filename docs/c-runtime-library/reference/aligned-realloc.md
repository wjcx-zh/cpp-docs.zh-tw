---
title: _aligned_realloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _aligned_realloc
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
- _aligned_realloc
- aligned_realloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_realloc function
- _aligned_realloc function
ms.assetid: 80ce96e8-6087-416f-88aa-4dbb8cb1d218
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb61143148a7d7e21c57f8130ffa9d789d8aa18
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="alignedrealloc"></a>_aligned_realloc

變更使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 所配置的記憶體區塊大小。

## <a name="syntax"></a>語法

```C
void * _aligned_realloc(
   void *memblock,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
目前記憶體區塊指標。

*size*<br/>
要求的記憶體配置的大小。

*對齊方式*<br/>
對齊值，必須是 2 的整數冪。

## <a name="return-value"></a>傳回值

**_aligned_realloc**傳回重新配置後 （且可能有移動） 記憶體區塊的 void 指標。 傳回值是**NULL**如果大小為零，且緩衝區引數不是**NULL**，或如果沒有足夠的可用記憶體將區塊展開為指定大小。 在第一種情況中，會釋放原始區塊。 在第二種情況中，原始區塊會保留不變。 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。

重新配置記憶體並變更區塊的對齊是不對的。

## <a name="remarks"></a>備註

**_aligned_realloc**根據**malloc**。 如需有關使用 **_aligned_offset_malloc**，請參閱[malloc](malloc.md)。

此函式會將**errno**至**ENOMEM**若記憶體配置失敗，或是要求的大小大於 **_HEAP_MAXREQ**。 如需有關**errno**，請參閱[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_realloc**會驗證其參數。 如果*對齊*不是乘為 2，此函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則此函數會傳回**NULL**並設定**errno**至**EINVAL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_aligned_realloc**|\<malloc.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>另請參閱

[資料對齊](../../c-runtime-library/data-alignment.md)<br/>
