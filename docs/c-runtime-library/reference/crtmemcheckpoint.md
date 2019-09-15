---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
api_name:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: edf91cd8c76fd080326e2e5eeac98f7f81ab90cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942373"
---
# <a name="_crtmemcheckpoint"></a>_CrtMemCheckpoint

取得 debug 堆積的目前狀態，並將存放區儲存在應用程式提供的 **_CrtMemState**結構中（僅限 debug 版本）。

## <a name="syntax"></a>語法

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>參數

*state*<br/>
要填入記憶體檢查點之 **_CrtMemState**結構的指標。

## <a name="remarks"></a>備註

**_CrtMemCheckpoint**函式會在任何指定的時間建立調試堆積目前狀態的快照集。 其他堆積狀態函式 (例如 [_CrtMemDifference](crtmemdifference.md) ) 可使用此快照協助偵測記憶體流失及其他問題。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtMemState**的呼叫。

應用程式必須將指標傳遞至先前配置的 **_CrtMemState**結構實例（定義于 crtdbg.h 裡中的*狀態*參數中）。 如果 **_CrtMemCheckpoint**在檢查點建立期間遇到錯誤，函式會產生描述問題的 **_CRT_WARN** debug 報告。

如需堆積狀態函數和 **_CrtMemState**結構的詳細資訊，請參閱[堆積狀態報表](/visualstudio/debugger/crt-debug-heap-details)函式。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如果*state*是**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)會設定為**EINVAL** ，而函式會傳回。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>、\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**磁帶**僅限 UCRT 的調試版本。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
