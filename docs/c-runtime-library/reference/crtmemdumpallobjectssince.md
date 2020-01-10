---
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
api_name:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: 9e3793e9b88c593968b108e2801e24476417603c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942376"
---
# <a name="_crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

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

**_CrtMemDumpAllObjectsSince**函式會以使用者可讀取的格式傾印堆積中所設定物件的 debug 標頭資訊。 應用程式會使用此傾印資訊追蹤配置及偵測記憶體問題。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtMemDumpAllObjectsSince**的呼叫。

**_CrtMemDumpAllObjectsSince**會使用*state*參數的值來決定要起始傾印作業的位置。 若要從指定的堆積狀態開始傾印， *state*參數必須是 **_CrtMemState**結構的指標，在呼叫 **_CrtMemDumpAllObjectsSince**之前已由[_CrtMemCheckpoint](crtmemcheckpoint.md)填入。 當*state*為**Null**時，函式會從程式執行開始時開始傾印。

如果應用程式藉由呼叫[_CrtSetDumpClient](crtsetdumpclient.md)來安裝傾印攔截函式，則每次 **_CrtMemDumpAllObjectsSince**傾印 **_CLIENT_BLOCK**類型之區塊的相關資訊時，就會呼叫應用程式提供的傾印函數。 根據預設，內部 C 執行時間區塊（ **_CRT_BLOCK**）不會包含在記憶體傾印作業中。 [_CrtSetDbgFlag](crtsetdbgflag.md)函數可以用來開啟 **_crtDbgFlag**的 **_CRTDBG_CHECK_CRT_DF**位，以包含這些區塊。 此外，標記為釋出或略過 ( **_FREE_BLOCK**、 **_IGNORE_BLOCK**) 的區塊不會包含在記憶體傾印中。

如需堆積狀態函數和 **_CrtMemState**結構的詳細資訊，請參閱[堆積狀態報表](/visualstudio/debugger/crt-debug-heap-details)函式。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需如何使用 **_CrtMemDumpAllObjectsSince**的範例，請參閱[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
