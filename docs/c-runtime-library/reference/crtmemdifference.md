---
title: _CrtMemDifference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27fb436c438daac7415ba3c0e7581611414c9c4a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="crtmemdifference"></a>_CrtMemDifference

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
指標 **_CrtMemState**結構用來儲存兩個記憶體狀態 （已傳回） 之間的差異。

*oldState*<br/>
較舊的記憶體狀態的指標 (**_CrtMemState**結構)。

*newState*<br/>
較新的記憶體狀態的指標 (**_CrtMemState**結構)。

## <a name="return-value"></a>傳回值

如果記憶體狀態明顯不同， **_CrtMemDifference** ，則傳回 TRUE。 否則，此函式會傳回 FALSE。

## <a name="remarks"></a>備註

**_CrtMemDifference**函式比較*oldState*和*newState* ，並將其差異*stateDiff*，如此可能再用於應用程式所偵測記憶體流失和其他記憶體問題。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，呼叫 **_CrtMemDifference**會在前置處理期間移除。

*newState*和*oldState*必須是有效的指標至 **_CrtMemState**結構，定義在 crtdbg.h 裡，有已填入[_CrtMemCheckpoint](crtmemcheckpoint.md)之前先呼叫 **_CrtMemDifference**。 *stateDiff*必須是先前配置的執行個體的指標 **_CrtMemState**結構。 如果*stateDiff*， *newState*，或*oldState*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)設**EINVAL**而且函數會傳回 FALSE。

**_CrtMemDifference**比較 **_CrtMemState**欄位值的區塊*oldState*中*newState* ，並將導致*stateDiff*。 當兩個記憶體狀態中的已配置區塊類型數目或配置給每種類型的區塊總數不同時，表示這兩個狀態有很大的差異。 曾經配置給在兩個狀態和總配置之間的差異也會儲存在兩個狀態的最大數量之間的差異*stateDiff*。

根據預設，內部 C 執行階段區塊 (**_CRT_BLOCK**) 不包含在記憶體狀態作業。 [_CrtSetDbgFlag](crtsetdbgflag.md)函式可用來開啟 **_CRTDBG_CHECK_CRT_DF**的位元 **_crtDbgFlag**若要將這些區塊包含在流失偵測和其他記憶體狀態作業。 釋放的記憶體區塊 (**_FREE_BLOCK**) 並不會造成 **_CrtMemDifference**傳回 TRUE。

如需堆積狀態函式和 **_CrtMemState**結構，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**程式庫：**僅限偵錯版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
