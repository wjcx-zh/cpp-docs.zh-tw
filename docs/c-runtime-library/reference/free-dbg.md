---
title: _free_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _free_dbg
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
- _free_dbg
- free_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa485eea6f0ffda05b0ef33a808d5ec837255514
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400040"
---
# <a name="freedbg"></a>_free_dbg

釋放堆積中的記憶體區塊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>參數

*userData*来釋放配置的記憶體區塊的指標。

*blockType*要釋放配置的記憶體區塊類型： **_CLIENT_BLOCK**， **_NORMAL_BLOCK**，或 **_IGNORE_BLOCK**。

## <a name="remarks"></a>備註

**_Free_dbg**函式是偵錯版本的[可用](free.md)函式。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，每次呼叫 **_free_dbg**呼叫會降**可用**。 同時**可用**和 **_free_dbg**釋放記憶體區塊，在基底堆積中，但 **_free_dbg**容納兩個偵錯功能： 釋放區塊保留在堆積中以模擬低記憶體狀況和釋放特定配置類型的區塊型別參數的連結的清單。

**_free_dbg**執行有效性檢查，對所有指定的檔案和區塊位置再執行釋放作業。 應用程式不需要提供此資訊。 釋放記憶體區塊時，偵錯堆積管理員會自動檢查使用者部分每一端的緩衝區完整性，並在發生覆寫時發出錯誤報表。 如果 **_CRTDBG_DELAY_FREE_MEM_DF**的位元欄位[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)設定旗標時，釋放的區塊填滿指定的值 0xDD， **_FREE_BLOCK**區塊類型，以及保留在堆積的連結清單的記憶體區塊。

如果發生錯誤時即釋放記憶體， **errno**設為從作業系統在本質上失敗的資訊。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需使用方式的範例 **_free_dbg**，請參閱[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
