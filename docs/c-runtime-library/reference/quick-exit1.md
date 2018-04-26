---
title: quick_exit1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- quick_exit
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
dev_langs:
- C++
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fde06fc83b27b8bba43e3fa929cc8b97bb68dd06
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="quickexit"></a>quick_exit

引發正常的程式終止。

## <a name="syntax"></a>語法

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>參數

*status*<br/>
要回傳給主機環境的狀態碼。

## <a name="return-value"></a>傳回值

**Quick_exit**函式無法傳回其呼叫端。

## <a name="remarks"></a>備註

**Quick_exit**函式會導致一般程式終止。 它會呼叫註冊沒有函式**atexit**， **_onexit**或訊號處理常式註冊**訊號**函式。 行為是未定義的如果**quick_exit**會呼叫超過一次，或如果**結束**也稱為函式。

**Quick_exit**函式呼叫，後進先出 (LIFO) 順序、 所註冊的函式中**at_quick_exit**，除了函式註冊時就已呼叫這些函式。  若在呼叫會終止函式呼叫的已註冊函式時定義了 [longjmp](longjmp.md)，則行為未定義。

已註冊的函式呼叫之後， **quick_exit**叫用 **_Exit**使用*狀態*將控制權交還給主機環境的值。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**quick_exit**|\<process.h> 或 \<stdlib.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
