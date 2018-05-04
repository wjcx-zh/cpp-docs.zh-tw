---
title: _onexit、_onexit_m | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _onexit
- _onexit_m
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
- _onexit
- onexit_m
- onexit
- _onexit_m
dev_langs:
- C++
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c190ce2c78135625a502d7509e56771fd670aa3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="onexit-onexitm"></a>_onexit，_onexit_m

在結束時註冊要呼叫的常式。

## <a name="syntax"></a>語法

```C
_onexit_t _onexit(
   _onexit_t function
);
_onexit_t_m _onexit_m(
   _onexit_t_m function
);
```

### <a name="parameters"></a>參數

*function*<br/>
結束時要呼叫的函式指標。

## <a name="return-value"></a>傳回值

**_onexit**函式傳回的指標，如果成功或**NULL**如果沒有函式指標儲存空間。

## <a name="remarks"></a>備註

**_Onexit**函式傳遞函式的位址 (*函式*) 正常程式終止時呼叫。 後續呼叫 **_onexit**建立 LIFO （最後一個中-後進先出） 的順序執行的函式的暫存器。 函式傳遞至 **_onexit**無法使用參數。

在案例時 **_onexit**向常式 DLL 中呼叫 **_onexit** DLL 上的執行的卸載之後**DllMain** DLL_PROCESS_DETACH 呼叫。

**_onexit**是 Microsoft 擴充功能。 針對 ANSI 可攜性，請使用 [atexit](atexit.md)。 **_Onexit_m**函式版本是混合的模式使用。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_onexit.c

#include <stdlib.h>
#include <stdio.h>

/* Prototypes */
int fn1(void), fn2(void), fn3(void), fn4 (void);

int main( void )
{
   _onexit( fn1 );
   _onexit( fn2 );
   _onexit( fn3 );
   _onexit( fn4 );
   printf( "This is executed first.\n" );
}

int fn1()
{
   printf( "next.\n" );
   return 0;
}

int fn2()
{
   printf( "executed " );
   return 0;
}

int fn3()
{
   printf( "is " );
   return 0;
}

int fn4()
{
   printf( "This " );
   return 0;
}
```

### <a name="output"></a>輸出

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
