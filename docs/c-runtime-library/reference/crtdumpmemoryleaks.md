---
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
apiname:
- _CrtDumpMemoryLeaks
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
ms.openlocfilehash: baf4f8d8234ba744acda20541d37bbc3ed076678
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531951"
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

發生記憶體流失時，傾印偵錯堆積中的所有記憶體區塊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>傳回值

**_CrtDumpMemoryLeaks**會傳回 TRUE，如果發現記憶體流失。 否則，此函式會傳回 FALSE。

## <a name="remarks"></a>備註

**_CrtDumpMemoryLeaks**函式會判斷自程式執行開始以來是否發生記憶體流失。 發現流失時，會以使用者可讀格式傾印堆積中所有物件的偵錯標頭資訊。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtDumpMemoryLeaks**會在前置處理期間移除。

**_CrtDumpMemoryLeaks**時經常會呼叫程式執行，以確認應用程式所配置的所有記憶體皆已都釋放的結尾。 呼叫此函數會自動在程式終止藉由開啟 **_CRTDBG_LEAK_CHECK_DF**位元欄位[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標使用[_CrtSetDbgFlag](crtsetdbgflag.md)函式。

**_CrtDumpMemoryLeaks**呼叫[_CrtMemCheckpoint](crtmemcheckpoint.md)取得堆積的目前狀態，然後掃描尚未釋放的區塊的狀態。 發生未的區塊時， **_CrtDumpMemoryLeaks**呼叫[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)傾印在程式執行開始從堆積中配置的所有物件的資訊。

根據預設，內部 C 執行階段區塊 (**_CRT_BLOCK**) 不會包含在記憶體傾印作業。 [_CrtSetDbgFlag](crtsetdbgflag.md)函式可用來開啟 **_CRTDBG_CHECK_CRT_DF**位元 **_crtDbgFlag**若要將這些區塊包含在流失偵測處理序。

如需堆積狀態函式和 **_CrtMemState**結構，請參閱[Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需如何使用的範例 **_CrtDumpMemoryLeaks**，請參閱[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
