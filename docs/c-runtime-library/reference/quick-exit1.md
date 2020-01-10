---
title: quick_exit1
ms.date: 11/04/2016
api_name:
- quick_exit
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 86246ed7a32dcd2f12b38aa4148570fc5fb3b7a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949677"
---
# <a name="quick_exit"></a>quick_exit

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

**Quick_exit**函式無法返回其呼叫端。

## <a name="remarks"></a>備註

**Quick_exit**函數會導致一般程式終止。 它不會呼叫由**信號**函數註冊的**atexit**、 **_onexit**或信號處理常式所註冊的任何函式。 如果呼叫**quick_exit**一次以上，或如果也呼叫**exit**函式，則會未定義行為。

**Quick_exit**函數會以後進先出（LIFO）順序呼叫**at_quick_exit**所註冊的函式，但函式註冊時已呼叫的函式除外。  若在呼叫先前已註冊，會終止函數呼叫的函式時呼叫 [longjmp](longjmp.md) ，其行為不確定。

呼叫已註冊的函式之後， **quick_exit**會使用*狀態值*叫用 **_Exit** ，以將控制權交還給主機環境。

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
