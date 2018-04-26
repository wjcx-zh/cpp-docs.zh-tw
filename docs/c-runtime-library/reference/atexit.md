---
title: atexit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a5dbe5e8bf71c268783893665e8e95bb587891a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

**Atexit**函式傳遞的函式位址*func*正常程式終止時呼叫。 後續呼叫**atexit**建立暫存器的順序執行後進先出 (LIFO) 的函式。 函式傳遞至**atexit**無法使用參數。 **atexit**和 **_onexit**來保存的暫存器的函式使用堆積。 因此，可以登錄的函式數目僅受限於堆積記憶體。

中的程式碼**atexit**函式不能包含任何相依性可能已經被卸載時的任何 DLL **atexit**呼叫函式。

產生符合 ANSI 標準的應用程式，請使用 ANSI 標準**atexit**函式 (而不是十分類似 **_onexit**函式)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>範例

此程式推入四個函式至函式時執行的堆疊**atexit**呼叫。 當程式結束時，這些程式會依後進先出的基礎執行。

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
