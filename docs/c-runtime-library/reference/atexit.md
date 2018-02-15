---
title: atexit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf87637fee2040bb5d1db05dd76e7e73728e375c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="atexit"></a>atexit
於結束時處理指定的函式。  
  
## <a name="syntax"></a>語法  
  
```  
int atexit(  
   void (__cdecl *func )( void )  
);  
```  
  
#### <a name="parameters"></a>參數  
 `func`  
 即將呼叫的函式。  
  
## <a name="return-value"></a>傳回值  
 若成功，則 `atexit` 傳回 0；若發生錯誤，則為非零值。  
  
## <a name="remarks"></a>備註  
 當程式正常終止時，會在呼叫函式的位址時 (`func`) 傳遞 `atexit` 函式。 後續呼叫 `atexit` 會建立依後進先出 (LIFO) 順序執行的函式的暫存器。 傳遞至 `atexit` 的函式不接受參數。 `atexit` 和 `_onexit` 使用堆積保存函式暫存器。 因此，可以登錄的函式數目僅受限於堆積記憶體。  
  
 `atexit` 函式中的程式碼不應包含對任何 DLL的相依性，DLL 可能已在呼叫 `atexit` 函式時卸載。  
  
 若要產生符合 ANSI 規範的應用程式，請使用 ANSI 標準 `atexit` 函式 (不是類似的 `_onexit` 函式)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`atexit`|\<stdlib.h>|  
  
## <a name="example"></a>範例  
 此程式會在呼叫 `atexit` 時將四個函式推入要執行的函式堆疊。 當程式結束時，這些程式會依後進先出的基礎執行。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)