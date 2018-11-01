---
title: _CrtMemDumpStatistics
ms.date: 11/04/2016
apiname:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
ms.openlocfilehash: 66eb58b65f3fa20e01ad16d68f3fe1baafd8cd04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605119"
---
# <a name="crtmemdumpstatistics"></a>_CrtMemDumpStatistics

針對採用使用者可讀格式的指定堆積狀態，傾印偵錯標頭資訊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>參數

*state*<br/>
要傾印的堆積狀態指標。

## <a name="remarks"></a>備註

**_CrtMemDumpStatistics**函式傾印堆積中的使用者可讀格式的指定狀態的偵錯標頭資訊。 應用程式會使用此傾印統計資料追蹤配置及偵測記憶體問題。 記憶體狀態可能包含特定堆積狀態或兩個狀態之間的差異。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtMemDumpStatistics**會在前置處理期間移除。

*狀態*參數必須是指標 **_CrtMemState**所填入的結構[_CrtMemCheckpoint](crtmemcheckpoint.md) ，或藉由傳回[_CrtMemDifference](crtmemdifference.md)之前 **_CrtMemDumpStatistics**呼叫。 如果*狀態*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為**EINVAL**和不採取任何動作。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如需堆積狀態函式和 **_CrtMemState**結構，請參閱[Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**程式庫：** 僅限偵錯版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
