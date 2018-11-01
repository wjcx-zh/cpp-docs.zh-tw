---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
apiname:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: ee435ba3e9e40795280dee0f97feaad32c8b0fc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589507"
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint

取得偵錯堆積的目前狀態，並將儲存在應用程式提供 **_CrtMemState**結構 （僅限偵錯版本）。

## <a name="syntax"></a>語法

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>參數

*state*<br/>
指標 **_CrtMemState**結構以填入記憶體檢查點。

## <a name="remarks"></a>備註

**_CrtMemCheckpoint**函式會建立偵錯堆積的目前狀態的快照集，在任何給定的時刻。 其他堆積狀態函式 (例如 [_CrtMemDifference](crtmemdifference.md) ) 可使用此快照協助偵測記憶體流失及其他問題。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtMemState**會在前置處理期間移除。

應用程式必須將指標傳遞至先前配置的執行個體 **_CrtMemState**結構，定義在 Crtdbg.h 中*狀態*參數。 如果 **_CrtMemCheckpoint**遇到錯誤，檢查點建立期間，函式會產生 **_CRT_WARN**偵錯報表，描述問題。

如需堆積狀態函式和 **_CrtMemState**結構，請參閱[Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如果*狀態*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)設為**EINVAL** ，函式傳回。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>、\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**程式庫：** 僅限 UCRT 的偵錯版本。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
