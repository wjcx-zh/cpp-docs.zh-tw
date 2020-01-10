---
title: _aligned_recalloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_recalloc_dbg
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
- _aligned_recalloc_dbg
- aligned_recalloc_dbg
helpviewer_keywords:
- aligned_recalloc_dbg function
- _aligned_recalloc_dbg function
ms.assetid: 55c3c27e-561c-4d6b-9bf9-1e34cc556e4b
ms.openlocfilehash: f322313557c41c0816fdd3b1e5ec89a50324beda
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944070"
---
# <a name="_aligned_recalloc_dbg"></a>_aligned_recalloc_dbg

變更使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void * _aligned_recalloc_dbg(
   void * memblock,
   size_t num,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
目前記憶體區塊指標。

*number*<br/>
元素數。

*size*<br/>
每個項目的大小 (位元組)。

*alignment*<br/>
對齊值，必須是 2 的整數冪。

*filename*<br/>
要求配置作業之原始程式檔的名稱的指標，或為**Null**。

*linenumber*<br/>
原始程式檔中的行號，其中要求配置作業，或**為 Null**。

## <a name="return-value"></a>傳回值

**_aligned_recalloc_dbg**會傳回已重新配置（且可能已移動）記憶體區塊的 void 指標。 如果大小為零，且緩衝區引數不是**null**，或如果沒有足夠的可用記憶體可將區塊展開為指定的大小，則傳回值會是**Null** 。 在第一種情況中，會釋放原始區塊。 在第二種情況中，原始區塊會保留不變。 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 Void 類型以外的指標，請對傳回值使用類型轉換。

重新配置記憶體並變更區塊的對齊是不對的。

## <a name="remarks"></a>備註

**_aligned_recalloc_dbg**是[_aligned_recalloc](aligned-recalloc.md)函數的調試版本。 未定義[_debug](../../c-runtime-library/debug.md)時，每個 **_aligned_recalloc_dbg**的呼叫都會縮減為 **_aligned_recalloc**的呼叫。 **_Aligned_recalloc**和 **_aligned_recalloc_dbg**都會重新配置基底堆積中的記憶體區塊，但 **_aligned_recalloc_dbg**會容納數個偵錯工具：在區塊的使用者部分的任一端使用緩衝區以測試洩漏和*filename* / *linenumber*資訊，以判斷配置要求的來源。 使用區塊類型參數追蹤特定的配置類型，並不是針對對齊配置所支援的偵錯工具功能。 對齊的配置會顯示為 _NORMAL_BLOCK 區塊類型。

**_aligned_recalloc_dbg**會重新配置指定的記憶體區塊，其空間會比要求的大小（*數位* * *大小*）稍微多一點，而且可能會大於或小於原先配置的記憶體區塊大小。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 重新配置可能會導致將原始記憶體區塊移到堆積中的不同位置，也可能會變更記憶體區塊的大小。 區塊的使用者部分會填入值 0xCD，且覆寫緩衝區會填入 0xFD。

如果記憶體配置失敗， **_aligned_recalloc_dbg**會將**Errno**設定為**ENOMEM** ;如果所需的記憶體數量（包括先前所述的額外負荷）超過 **_HEAP_MAXREQ**，則會傳回**EINVAL** 。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

此外， **_aligned_recalloc_dbg**會驗證其參數。 如果*對齊*不是2的乘冪，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回**Null** ，並將**Errno**設為**EINVAL**。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_aligned_recalloc_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
