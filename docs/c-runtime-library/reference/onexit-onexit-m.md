---
title: _onexit，_onexit_m
ms.date: 11/04/2016
api_name:
- _onexit
- _onexit_m
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
ms.openlocfilehash: 9afcd729f19f11b82e8f24c2b7fcf9ec40990deb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951350"
---
# <a name="_onexit-_onexit_m"></a>_onexit，_onexit_m

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

如果成功， **_onexit**會傳回函式的指標，如果沒有空間可儲存函式指標，則會傳回**Null** 。

## <a name="remarks"></a>備註

當程式正常終止時，會傳遞要呼叫之函式（函*式）的*位址給 **_onexit**函式。 後續對 **_onexit**的呼叫會建立以 LIFO （後進先出）循序執行的函式的註冊。 傳遞至 **_onexit**的函式不能接受參數。

在從 DLL 內呼叫 **_onexit**的情況下，使用 **_onexit**註冊的常式會在使用 DLL_PROCESS_DETACH 呼叫**DllMain**之後，于 dll 的卸載上執行。

**_onexit**是 Microsoft 擴充功能。 針對 ANSI 可攜性，請使用 [atexit](atexit.md)。 函式的 **_onexit_m**版本適用于混合模式使用。

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

### <a name="output"></a>Output

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
