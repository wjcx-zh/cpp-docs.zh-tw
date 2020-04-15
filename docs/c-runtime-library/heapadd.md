---
title: _heapadd
ms.date: 11/04/2016
api_name:
- _heapadd
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapadd
- _heapadd
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
ms.openlocfilehash: c5eeb66ff0e6fb05063ec395e12cd97106ad724d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351324"
---
# <a name="_heapadd"></a>_heapadd

將記憶體加入堆積。

> [!IMPORTANT]
> 此函式已過時。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。

## <a name="syntax"></a>語法

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>參數

*memblock*<br/>
指向堆積記憶體的指標。

*大小*<br/>
要加入的記憶體大小 (位元組)。

## <a name="return-value"></a>傳回值

若成功，`_heapadd` 會傳回 0；否則此函式會傳回 -1，並將 `errno` 設為 `ENOSYS`。

如需此函式與其他傳回碼的詳細資訊，請參閱 [_doserrno, errno、_sys_errlist 及 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

自 Visual C++ 4.0 版起，基礎堆積結構已移到 C 執行階段程式庫，以支援新的偵錯功能。 因此，所有採用 Win32 API 的平台將不再支援 `_heapadd` 。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|`_heapadd`|\<malloc.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱簡介中的 [Compatibility](../c-runtime-library/compatibility.md) 。

## <a name="see-also"></a>另請參閱

[記憶體配置](../c-runtime-library/memory-allocation.md)<br/>
[自由](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
