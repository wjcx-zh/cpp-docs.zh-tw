---
title: _CrtGetReportHook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtGetReportHook
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
- CrtGetReportHook
- _CrtGetReportHook
dev_langs:
- C++
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b1e499b1663cbde3bcaa0a01a26e96d544ca390
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="crtgetreporthook"></a>_CrtGetReportHook

擷取用戶端定義的報告函式，以將它連結到偵錯報告處理序的 C 執行階段 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
_CRT_REPORT_HOOK _CrtGetReportHook( void );
```

## <a name="return-value"></a>傳回值

傳回目前的用戶端定義報告函式。

## <a name="remarks"></a>備註

**_CrtGetReportHook**可讓應用程式擷取目前報告的函式，C 執行階段偵錯程式庫報告程序。

如需使用支援攔截程序之其他執行階段函式，以及撰寫您自己的用戶端定義攔截函式的詳細資訊，請參閱[撰寫偵錯攔截函式](/visualstudio/debugger/debug-hook-function-writing)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_CrtGetReportHook**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需使用方式的範例 **_CrtSetReportHook**，請參閱[報表](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/report)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportHook](crtsetreporthook.md)<br/>
