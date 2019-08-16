---
title: _get_heap_handle
ms.date: 11/04/2016
apiname:
- _get_heap_handle
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
- _get_heap_handle
- get_heap_handle
helpviewer_keywords:
- heap functions
- memory allocation, heap memory
- _get_heap_handle function
- get_heap_handle function
ms.assetid: a4d05049-8528-494a-8281-a470d1e1115c
ms.openlocfilehash: 7e82686c4b33dc11f02f387a97966d3ff5a47085
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499920"
---
# <a name="_get_heap_handle"></a>_get_heap_handle

傳回 C 執行階段系統所使用之堆積的控制代碼。

## <a name="syntax"></a>語法

```C
intptr_t _get_heap_handle( void );
```

## <a name="return-value"></a>傳回值

將控制代碼傳回至 C 執行階段系統所使用的 Win32 堆積。

## <a name="remarks"></a>備註

如果您想要呼叫 [HeapSetInformation](/windows/win32/api/heapapi/nf-heapapi-heapsetinformation) 並在 CRT 堆積上啟用低分散堆積，請使用這個函式。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_heap_handle**|\<malloc.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="sample"></a>範例

```cpp
// crt_get_heap_handle.cpp
// compile with: /MT
#include <windows.h>
#include <malloc.h>
#include <stdio.h>

int main(void)
{
    intptr_t hCrtHeap = _get_heap_handle();
    ULONG ulEnableLFH = 2;
    if (HeapSetInformation((PVOID)hCrtHeap,
                           HeapCompatibilityInformation,
                           &ulEnableLFH, sizeof(ulEnableLFH)))
        puts("Enabling Low Fragmentation Heap succeeded");
    else
        puts("Enabling Low Fragmentation Heap failed");
    return 0;
}
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
