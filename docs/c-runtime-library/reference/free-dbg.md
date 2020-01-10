---
title: _free_dbg
ms.date: 11/04/2016
api_name:
- _free_dbg
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
- _free_dbg
- free_dbg
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
ms.openlocfilehash: 43591ce8710dd25ad33832a5f084ca6e84bba979
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956798"
---
# <a name="_free_dbg"></a>_free_dbg

釋放堆積中的記憶體區塊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>參數

*userData*<br/>
要釋放之已配置記憶體區塊的指標。

*blockType*<br/>
要釋放的已配置記憶體區塊類型： **_CLIENT_BLOCK**、 **_NORMAL_BLOCK**或 **_IGNORE_BLOCK**。

## <a name="remarks"></a>備註

**_Free_dbg**函數是[free](free.md)函式的 debug 版本。 未定義[_debug](../../c-runtime-library/debug.md)時，每個 **_free_dbg**的呼叫都會縮減為**免費**的呼叫。 **Free**和 **_free_dbg**都會釋放基底堆積中的記憶體區塊，但 **_free_dbg**會容納兩個偵錯工具：將釋放的區塊保留在堆積的連結清單中，以模擬記憶體不足的狀況，並將區塊類型參數設為免費的特定配置類型。

在執行免費作業之前， **_free_dbg**會對所有指定的檔案和區塊位置執行有效性檢查。 應用程式不需要提供此資訊。 釋放記憶體區塊時，偵錯堆積管理員會自動檢查使用者部分每一端的緩衝區完整性，並在發生覆寫時發出錯誤報表。 如果已設定[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標的 **_CRTDBG_DELAY_FREE_MEM_DF**位欄位，釋放的區塊會填入值0xDD、指派 **_FREE_BLOCK**區塊類型，並保留在堆積的記憶體區塊連結清單中。

如果釋放記憶體時發生錯誤，則會在失敗的本質中，使用作業系統的資訊來設定**errno** 。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需如何使用 **_free_dbg**的範例，請參閱[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
