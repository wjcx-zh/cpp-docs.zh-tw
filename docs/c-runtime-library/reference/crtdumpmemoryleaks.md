---
title: _CrtDumpMemoryLeaks | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb0ebfe1017f6315d60528c5f6196131704c5d0f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

發生記憶體流失時，傾印偵錯堆積中的所有記憶體區塊 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>傳回值

**_CrtDumpMemoryLeaks**傳回 TRUE，如果找到記憶體流失。 否則，此函式會傳回 FALSE。

## <a name="remarks"></a>備註

**_CrtDumpMemoryLeaks**函式判斷是否執行程式啟動之後發生記憶體流失。 發現流失時，會以使用者可讀格式傾印堆積中所有物件的偵錯標頭資訊。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，呼叫 **_CrtDumpMemoryLeaks**會在前置處理期間移除。

**_CrtDumpMemoryLeaks**經常稱為結尾的程式執行，以確認被釋出所有應用程式所配置的記憶體。 呼叫此函數會自動在程式終止藉由開啟 **_CRTDBG_LEAK_CHECK_DF**的位元欄位[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標使用[_CrtSetDbgFlag](crtsetdbgflag.md)函式。

**_CrtDumpMemoryLeaks**呼叫[_CrtMemCheckpoint](crtmemcheckpoint.md)取得堆積的目前狀態，然後掃描尚未釋放的區塊的狀態。 當遇到 unfreed 的區塊時， **_CrtDumpMemoryLeaks**呼叫[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)傾印的程式執行開始從堆積中配置的所有物件的資訊。

根據預設，內部 C 執行階段區塊 (**_CRT_BLOCK**) 不包含在記憶體傾印作業。 [_CrtSetDbgFlag](crtsetdbgflag.md)函式可用來開啟 **_CRTDBG_CHECK_CRT_DF**的位元 **_crtDbgFlag**若要將這些區塊包含在流失偵測處理程序。

如需堆積狀態函式和 **_CrtMemState**結構，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需使用方式的範例 **_CrtDumpMemoryLeaks**，請參閱[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
