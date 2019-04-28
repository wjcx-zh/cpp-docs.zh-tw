---
title: quick_exit1
ms.date: 11/04/2016
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
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 50f1ee72cce04c2bebc8f7396a2b6fad98301dd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358030"
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

**Quick_exit**函式無法傳回至其呼叫端。

## <a name="remarks"></a>備註

**Quick_exit**函式會導致正常程式終止。 它會呼叫註冊的任何函式**atexit**， **_onexit**或訊號處理常式註冊**訊號**函式。 行為是未定義的如果**quick_exit**稱為超過一次，或如果**結束**也呼叫函式。

**Quick_exit**函式呼叫，在後進先出 (LIFO) 順序、 註冊的函式**at_quick_exit**，但函式註冊時就已呼叫這些函式。  若在呼叫先前已註冊，會終止函數呼叫的函式時呼叫 [longjmp](longjmp.md) ，其行為不確定。

已註冊的函式呼叫之後， **quick_exit**叫用 **_Exit**利用*狀態*將控制權交還給主機環境的值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
