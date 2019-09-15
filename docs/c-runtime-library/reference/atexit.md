---
title: atexit
ms.date: 11/04/2016
api_name:
- atexit
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
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: b91e6dad81f006b0b94ac17a940e840386f6d2b1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939652"
---
# <a name="atexit"></a>atexit

於結束時處理指定的函式。

## <a name="syntax"></a>語法

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>參數

*func*<br/>
即將呼叫的函式。

## <a name="return-value"></a>傳回值

如果成功， **atexit**會傳回0，如果發生錯誤，則傳回非零值。

## <a name="remarks"></a>備註

當程式正常終止時，會將函式*func*的位址傳遞給**atexit**函式，以呼叫該函數。 後續的**atexit**呼叫會建立以後進先出（LIFO）循序執行之函式的註冊。 傳遞至**atexit**的函式不能接受參數。 **atexit**和 **_onexit**會使用堆積來保存函數的暫存器。 因此，可以登錄的函式數目僅受限於堆積記憶體。

**Atexit**函式中的程式碼不應包含任何可能已在呼叫**atexit**函式時卸載之 DLL 的相依性。

若要產生符合 ANSI 規範的應用程式，請使用 ANSI 標準**atexit**函數（而不是類似的 **_onexit**函數）。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>範例

此程式會將四個函數推送至呼叫**atexit**時所要執行的函式堆疊。 當程式結束時，這些程式會依後進先出的基礎執行。

```C
// crt_atexit.c
#include <stdlib.h>
#include <stdio.h>

void fn1( void ), fn2( void ), fn3( void ), fn4( void );

int main( void )
{
   atexit( fn1 );
   atexit( fn2 );
   atexit( fn3 );
   atexit( fn4 );
   printf( "This is executed first.\n" );
}

void fn1()
{
   printf( "next.\n" );
}

void fn2()
{
   printf( "executed " );
}

void fn3()
{
   printf( "is " );
}

void fn4()
{
   printf( "This " );
}
```

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
