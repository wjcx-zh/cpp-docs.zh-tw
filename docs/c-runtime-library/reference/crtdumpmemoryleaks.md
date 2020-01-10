---
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
api_name:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
ms.openlocfilehash: dae93577f5c0c0297606577c05d6b6ef2040c831
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938822"
---
# <a name="_crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

發生記憶體流失時，傾印偵錯堆積中的所有記憶體區塊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>傳回值

如果找到記憶體流失，則 **_CrtDumpMemoryLeaks**會傳回 TRUE。 否則，此函式會傳回 FALSE。

## <a name="remarks"></a>備註

**_CrtDumpMemoryLeaks**函式會判斷自程式執行開始後是否發生記憶體流失。 發現流失時，會以使用者可讀格式傾印堆積中所有物件的偵錯標頭資訊。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtDumpMemoryLeaks**的呼叫。

在程式執行結束時經常會呼叫 **_CrtDumpMemoryLeaks** ，以確認已釋放應用程式所配置的所有記憶體。 在程式終止時，可以使用[_CrtSetDbgFlag](crtsetdbgflag.md)函式來開啟[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標的 **_CRTDBG_LEAK_CHECK_DF**位欄位，以自動呼叫函式。

**_CrtDumpMemoryLeaks**會呼叫[_CrtMemCheckpoint](crtmemcheckpoint.md)以取得堆積的目前狀態，然後掃描尚未釋放之區塊的狀態。 遇到 unfreed 區塊時， **_CrtDumpMemoryLeaks**會呼叫[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) ，從程式執行開始時，傾印堆積中配置的所有物件的資訊。

根據預設，內部 C 執行時間區塊（ **_CRT_BLOCK**）不會包含在記憶體傾印作業中。 [_CrtSetDbgFlag](crtsetdbgflag.md)函式可用來開啟 **_CRTDBG_CHECK_CRT_DF**位的 **_crtDbgFlag** ，以將這些區塊包含在流失偵測進程中。

如需堆積狀態函數和 **_CrtMemState**結構的詳細資訊，請參閱[堆積狀態報表](/visualstudio/debugger/crt-debug-heap-details)函式。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需如何使用 **_CrtDumpMemoryLeaks**的範例，請參閱[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
