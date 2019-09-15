---
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_malloc_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 4fbacb170fd1ae1ce92de4a11ea85ff42b3942a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939776"
---
# <a name="_aligned_offset_malloc_dbg"></a>_aligned_offset_malloc_dbg

在指定的對齊界限上配置記憶體 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*size*<br/>
要求的記憶體配置的大小。

*alignment*<br/>
對齊值，必須是 2 的整數冪。

*offset*<br/>
記憶體配置中要強制對齊的位移。

*filename*<br/>
要求配置作業之原始程式檔的名稱的指標，或為**Null**。

*linenumber*<br/>
原始程式檔中的行號，其中要求配置作業，或**為 Null**。

## <a name="return-value"></a>傳回值

已配置之記憶體區塊的指標，如果作業失敗，則為**Null** 。

## <a name="remarks"></a>備註

**_aligned_offset_malloc_dbg**是[_aligned_offset_malloc](aligned-offset-malloc.md)函數的調試版本。 未定義[_debug](../../c-runtime-library/debug.md)時，每個 **_aligned_offset_malloc_dbg**的呼叫都會縮減為 **_aligned_offset_malloc**的呼叫。 **_Aligned_offset_malloc**和 **_aligned_offset_malloc_dbg**都是在基底堆積中配置記憶體區塊，但 **_aligned_offset_malloc_dbg**提供了數個調試功能：在區塊的使用者部分的任一端使用緩衝區，測試流失和*filename* / *linenumber*資訊，以判斷配置要求的來源。 使用區塊類型參數追蹤特定的配置類型，並不是針對對齊配置所支援的偵錯工具功能。 對齊的配置會顯示為 _NORMAL_BLOCK 區塊類型。

**_aligned_offset_malloc_dbg**會以比所要求*大小*稍微多一點的空間來配置記憶體區塊。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。

當嵌套元素需要對齊時， **_aligned_offset_malloc_dbg**會很有用;例如，如果在嵌套類別上需要對齊。

**_aligned_offset_malloc_dbg**是以**malloc**為基礎;如需詳細資訊，請參閱[malloc](malloc.md)。

如果記憶體配置失敗，或是要求的大小大於 **_HEAP_MAXREQ**，則此函式會將**Errno**設定為**ENOMEM** 。 如需**errno**的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外， **_aligned_offset_malloc**會驗證其參數。 如果*對齊*不是2的乘冪，或*offset*大於或等於 size 和非零*值*，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回**Null** ，並將**Errno**設為**EINVAL**。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如需配置區塊類型和其使用方式的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
