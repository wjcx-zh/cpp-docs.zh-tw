---
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: 7de0ee9ff166af6336a8d14aa0dbd07dbd7d23fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526044"
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

從程式執行一開始，或從指定的堆積狀態傾印堆積中物件的相關資訊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>參數

*state*<br/>
要開始傾印之來源堆積狀態的指標，或為 **NULL**。

## <a name="remarks"></a>備註

**_CrtMemDumpAllObjectsSince**函式傾印偵錯標頭資訊的使用者可讀的格式中的堆積中配置的物件。 應用程式會使用此傾印資訊追蹤配置及偵測記憶體問題。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtMemDumpAllObjectsSince**會在前置處理期間移除。

**_CrtMemDumpAllObjectsSince**會使用值*狀態*參數，來判斷起始傾印作業的位置。 若要開始從指定的堆積狀態，傾印*狀態*參數必須是指標 **_CrtMemState**所填入的結構[_CrtMemCheckpoint](crtmemcheckpoint.md)之前 **_CrtMemDumpAllObjectsSince**呼叫。 當*狀態*是**NULL**，函數會開始從程式執行開始傾印。

如果應用程式已安裝的傾印攔截函式，藉由呼叫[_CrtSetDumpClient](crtsetdumpclient.md)，則每次 **_CrtMemDumpAllObjectsSince**傾印資訊有關 **_CLIENT_BLOCK**類型的區塊，它會呼叫應用程式所提供的傾印函式。 根據預設，內部 C 執行階段區塊 (**_CRT_BLOCK**) 不會包含在記憶體傾印作業。 [_CrtSetDbgFlag](crtsetdbgflag.md)函式可用來開啟 **_CRTDBG_CHECK_CRT_DF**位元 **_crtDbgFlag**以包含這些區塊。 此外，標記為釋出或略過 (**_FREE_BLOCK**、**_IGNORE_BLOCK**) 的區塊不會包含在記憶體傾印中。

如需堆積狀態函式和 **_CrtMemState**結構，請參閱[Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需如何使用的範例 **_CrtMemDumpAllObjectsSince**，請參閱[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
