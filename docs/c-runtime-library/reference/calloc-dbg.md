---
title: _calloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a00faae2ee66f22c7662ddd5926131b0e0347de
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="callocdbg"></a>_calloc_dbg

使用額外空間為偵錯標頭和覆寫緩衝區配置堆積中的記憶體區塊數目 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*數字*<br/>
要求的記憶體區塊數。

*size*<br/>
要求的每個記憶體區塊大小 (位元組)。

*blockType*<br/>
要求的記憶體區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

如需配置區塊類型和其使用方式的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

*filename*<br/>
要求配置作業之原始程式檔名稱的指標或**NULL**。

*linenumber*<br/>
要求配置作業，原始程式檔中的行號或**NULL**。

*Filename*和*linenumber*參數時，就只能使用 **_calloc_dbg**明確呼叫或[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)已定義前置處理器常數。

## <a name="return-value"></a>傳回值

成功完成時，此函式傳回最後一個配置的記憶體區塊的使用者部分的指標，呼叫新的處理常式函式，或傳回**NULL**。 如需傳回行為的完整描述，請參閱＜備註＞一節。 如需如何使用新的處理常式函式的詳細資訊，請參閱 [calloc](calloc.md) 函式。

## <a name="remarks"></a>備註

**_calloc_dbg**是偵錯版本的[calloc](calloc.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，每次呼叫 **_calloc_dbg**呼叫會降**calloc**。 同時**calloc**和 **_calloc_dbg**配置*數目*記憶體會封鎖在基底堆積中，但 **_calloc_dbg**提供數個偵錯功能：

- 區塊之使用者部分任一端上要測試流失的緩衝區。

- 追蹤特定配置類型的區塊類型參數。

- *檔名*/*linenumber*判斷配置要求來源的資訊。

**_calloc_dbg**配置比要求稍微多一些的空間與每個記憶體區塊*大小*。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。

**_calloc_dbg**設定**errno**至**ENOMEM**記憶體配置失敗。**EINVAL**傳回如果需要的記憶體數量 （包含之前提到的額外負荷） 超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式與其偵錯版本間之差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
