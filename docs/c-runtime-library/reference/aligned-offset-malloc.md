---
title: _aligned_offset_malloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_malloc
- _o__aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 1f13afbab75d2926d1c642c1430a3ffe5ecbac8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350580"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

針對指定的對齊界限配置記憶體。

## <a name="syntax"></a>語法

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>參數

*大小*<br/>
要求的記憶體配置的大小。

*對齊*<br/>
對齊值，必須是 2 的整數冪。

*位移*<br/>
記憶體配置中要強制對齊的位移。

## <a name="return-value"></a>傳回值

如果操作失敗,指向已分配的記憶體區塊的指標或**NULL。**

## <a name="remarks"></a>備註

在嵌套元素上需要對齊的情況下 **,_aligned_offset_malloc**非常有用;例如,如果嵌套類上需要對齊。

**_aligned_offset_malloc**以**馬婁克**為基礎。有關詳細資訊,請參閱[malloc](malloc.md)。

**_aligned_offset_malloc**標記`__declspec(noalias)`為`__declspec(restrict)`, 表示保證函數不修改全域變數,並且返回的指標不會別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

如果記憶體分配失敗或請求的大小大於 **_HEAP_MAXREQ,** 此函數將**errno**設置**到 ENOMEM。** 有關**errno**的詳細資訊,請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外 **,_aligned_offset_malloc**驗證其參數。 如果*對齊*不是 2 的功率,或者如果*偏移*量大於或等於*大小*和非零,則此函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則此函數將傳回**NULL**並將**errno**設定到**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>另請參閱

[資料對齊](../../c-runtime-library/data-alignment.md)<br/>
