---
title: _CrtDbgBreak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtDbgBreak
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
- _CrtDbgBreak
- CrtDbgBreak
dev_langs:
- C++
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d63795ec929fe1333bfc0d55acc307b52d559faf
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="crtdbgbreak"></a>_CrtDbgBreak

在特定程式碼行上設定中斷點 (僅適用於偵錯模式)。

## <a name="syntax"></a>語法

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>傳回值

沒有傳回值。

## <a name="remarks"></a>備註

**_CrtDbgBreak**函式會將偵錯中斷點上特定程式碼行所在的函式。 此函式用於僅限偵錯模式而且相依於 **_DEBUG**先前所定義。

如需使用支援攔截程序之其他執行階段函式，以及撰寫您自己的用戶端定義攔截函式的詳細資訊，請參閱[撰寫您自己的偵錯攔截函式](/visualstudio/debugger/debug-hook-function-writing)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_CrtDbgBreak**|\<CRTDBG.h>|

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[__debugbreak](../../intrinsics/debugbreak.md)<br/>
