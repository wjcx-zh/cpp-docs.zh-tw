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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b27f5000a48ec3aafe37c6bd59e9b9acddd5bec5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350567"
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

*大小*<br/>
記憶體配置的大小。

*對齊*<br/>
對齊值，必須是 2 的整數冪。

*位移*<br/>
記憶體配置中要強制對齊的位移。

## <a name="return-value"></a>傳回值

**_aligned_offset_realloc**返回指向重新分配(並可能移動)記憶體塊的空指標。 如果大小為零且緩衝區參數不是**NULL,** 或者沒有足夠的可用記憶體將塊擴展到給定大小,則返回值為**NULL。** 在第一種情況中，會釋放原始區塊。 在第二種情況中，原始區塊會保留不變。 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。

**_aligned_offset_realloc**標記`__declspec(noalias)`為`__declspec(restrict)`, 表示保證函數不修改全域變數,並且返回的指標不會別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

## <a name="remarks"></a>備註

與[_aligned_offset_malloc](aligned-offset-malloc.md)一樣 **,_aligned_offset_realloc**允許在結構內的偏移量下對齊結構。

**_aligned_offset_realloc**是以**馬婁克**為基地的。 有關使用 **_aligned_offset_malloc**的詳細資訊,請參閱[malloc](malloc.md)。 如果*memblock*為**NULL,** 則函數在內部呼叫 **_aligned_offset_malloc。**

如果記憶體分配失敗或請求的大小大於 **_HEAP_MAXREQ,** 此函數將**errno**設置**到 ENOMEM。** 有關**errno**的詳細資訊,請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外 **,_aligned_offset_realloc**驗證其參數。 如果*對齊*不是 2 的功率,或者如果*偏移*量大於或等於*大小*和非零,則此函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則此函數將傳回**NULL**並將**errno**設定到**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>另請參閱

[資料對齊](../../c-runtime-library/data-alignment.md)<br/>
