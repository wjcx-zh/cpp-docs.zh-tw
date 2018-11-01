---
title: _onexit，_onexit_m
ms.date: 11/04/2016
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
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
ms.openlocfilehash: c190f777032904802f771bab9fc323ba305ff32e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609597"
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

**_onexit**函式傳回的指標，如果是成功或是**NULL**如果沒有空間可儲存函式指標。

## <a name="remarks"></a>備註

**_Onexit**函式的位址傳遞給函式 (*函式*) 當程式正常終止時呼叫。 後續呼叫 **_onexit**建立依 LIFO （最後一個-後進先出） 順序執行的函式的暫存器。 函式傳遞至 **_onexit**不能接受參數。

萬一時 **_onexit** DLL 時，註冊的常式中呼叫 **_onexit**執行於 DLL 卸載之後**DllMain**在使用 DLL_PROCESS_DETACH 呼叫。

**_onexit**是 Microsoft 擴充功能。 針對 ANSI 可攜性，請使用 [atexit](atexit.md)。 **_Onexit_m**函式版本是適用於混合的模式。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
