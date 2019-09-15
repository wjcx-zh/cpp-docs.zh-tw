---
title: _CrtMemDifference
ms.date: 11/04/2016
api_name:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: 51bfa014d54f55843fcb112f318f143774abf8f3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938702"
---
# <a name="_crtmemdifference"></a>_CrtMemDifference

比較兩個記憶體狀態並傳回其差異 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
int _CrtMemDifference(
   _CrtMemState *stateDiff,
   const _CrtMemState *oldState,
   const _CrtMemState *newState
);
```

### <a name="parameters"></a>參數

*stateDiff*<br/>
**_CrtMemState**結構的指標，用來儲存兩個記憶體狀態（已傳回）之間的差異。

*oldState*<br/>
較舊記憶體狀態（ **_CrtMemState**結構）的指標。

*newState*<br/>
較新記憶體狀態（ **_CrtMemState**結構）的指標。

## <a name="return-value"></a>傳回值

如果記憶體狀態明顯不同，則 **_CrtMemDifference**會傳回 TRUE。 否則，此函式會傳回 FALSE。

## <a name="remarks"></a>備註

**_CrtMemDifference**函式會比較*oldState*和*newState* ，並將其差異儲存在*stateDiff*中，應用程式可以使用此功能來偵測記憶體流失和其他記憶體問題。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtMemDifference**的呼叫。

*newState*和*OldState*必須是 **_CrtMemState**結構的有效指標（定義于 crtdbg.h 裡中），而且在呼叫 **_CrtMemCheckpoint**之前已由[_CrtMemDifference](crtmemcheckpoint.md)填入。 *stateDiff*必須是先前配置的 **_CrtMemState**結構實例的指標。 如果*stateDiff*、 *newState*或*oldState*是**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)會設定為**EINVAL** ，而此函數會傳回 FALSE。

**_CrtMemDifference**會比較*oldState*中區塊的 **_CrtMemState**域值與*newState*中的區塊，並將結果儲存在*stateDiff*中。 當兩個記憶體狀態中的已配置區塊類型數目或配置給每種類型的區塊總數不同時，表示這兩個狀態有很大的差異。 曾經配置給這兩個狀態的最大數量，以及兩個狀態的總配置之間的差異，也會儲存在*stateDiff*中。

根據預設，內部 C 執行時間區塊（ **_CRT_BLOCK**）不會包含在記憶體狀態作業中。 [_CrtSetDbgFlag](crtsetdbgflag.md)函式可用來開啟 **_CRTDBG_CHECK_CRT_DF**位的 **_crtDbgFlag** ，以將這些區塊包含在流失偵測和其他記憶體狀態作業中。 釋放的記憶體區塊（ **_FREE_BLOCK**）不會導致 **_CrtMemDifference**傳回 TRUE。

如需堆積狀態函數和 **_CrtMemState**結構的詳細資訊，請參閱[堆積狀態報表](/visualstudio/debugger/crt-debug-heap-details)函式。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**磁帶**僅限[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)的 Debug 版本。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
