---
title: atexit
ms.date: 11/04/2016
apiname:
- atexit
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
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: 48f0fbfa1f3350f73899fcdbb3bf7922f1c6174d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556635"
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

**atexit**傳回 0，如果成功或為非零值，如果發生錯誤。

## <a name="remarks"></a>備註

**Atexit**函式的位址傳遞給函式*func*當程式正常終止時呼叫。 後續呼叫**atexit**建立後進先出 (LIFO) 順序執行的函式的暫存器。 函式傳遞至**atexit**不能接受參數。 **atexit**並 **_onexit**使用堆積保存函式暫存器。 因此，可以登錄的函式數目僅受限於堆積記憶體。

中的程式碼**atexit**函式不應包含的任何相依性可能已卸載時的任何 DLL **atexit**呼叫函式。

若要產生符合 ANSI 標準的應用程式，使用 ANSI 標準**atexit**函式 (不是類似 **_onexit**函式)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>範例

此程式的推播四個函式時執行的函式的堆疊**atexit**呼叫。 當程式結束時，這些程式會依後進先出的基礎執行。

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
