---
title: _aligned_offset_realloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_realloc
- _o__aligned_offset_realloc
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
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: c719f62a089b1c233bac193f3431d0375af826eb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910253"
---
# <a name="_aligned_offset_realloc"></a>_aligned_offset_realloc

變更使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 所配置的記憶體區塊大小。

## <a name="syntax"></a>語法

```C
void * _aligned_offset_realloc(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
目前記憶體區塊指標。

*size*<br/>
記憶體配置的大小。

*對齊*<br/>
對齊值，必須是 2 的整數冪。

*offset*<br/>
記憶體配置中要強制對齊的位移。

## <a name="return-value"></a>傳回值

**_aligned_offset_realloc**會傳回已重新配置（且可能已移動）記憶體區塊的 void 指標。 如果大小為零，且緩衝區引數不是**null**，或如果沒有足夠的可用記憶體可將區塊展開為指定的大小，則傳回值會是**Null** 。 在第一種情況中，會釋放原始區塊。 在第二種情況中，原始區塊會保留不變。 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。

**_aligned_offset_realloc**標示`__declspec(noalias)`為和`__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

## <a name="remarks"></a>備註

如同[_aligned_offset_malloc](aligned-offset-malloc.md)， **_aligned_offset_realloc**可讓結構在結構內的位移對齊。

**_aligned_offset_realloc**是以**malloc**為基礎。 如需使用 **_aligned_offset_malloc**的詳細資訊，請參閱[malloc](malloc.md)。 如果*memblock*為**Null**，則函式會在內部呼叫 **_aligned_offset_malloc** 。

如果記憶體配置失敗，或是要求的大小大於 **_HEAP_MAXREQ**，則此函式會將**Errno**設定為**ENOMEM** 。 如需**errno**的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_realloc**會驗證其參數。 如果*對齊*不是2的乘冪，或*offset*大於或等於 size 和非零*值*，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回**Null** ，並將**Errno**設為**EINVAL**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>另請參閱

[資料對齊](../../c-runtime-library/data-alignment.md)<br/>
