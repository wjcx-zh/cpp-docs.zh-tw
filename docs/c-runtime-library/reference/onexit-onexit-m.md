---
title: "_onexit、_onexit_m | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: caa4c732449864c4803a25f3bb123c43495f5fc1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="onexit-onexitm"></a>_onexit，_onexit_m
在結束時註冊要呼叫的常式。  
  
## <a name="syntax"></a>語法  
  
```  
_onexit_t _onexit(  
   _onexit_t function  
);  
_onexit_t_m _onexit_m(  
   _onexit_t_m function  
);  
```  
  
#### <a name="parameters"></a>參數  
 `function`  
 結束時要呼叫的函式指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，`_onexit` 會傳回函式的指標；如果沒有空間可儲存函式指標，則為 `NULL`。  
  
## <a name="remarks"></a>備註  
 當程式正常終止時，會將要呼叫之函式 (`function`) 的位址傳遞給 `_onexit` 函式。 後續呼叫 `_onexit` 會建立依 LIFO (後進先出) 順序執行之函式的暫存器。 傳遞至 `_onexit` 的函式不接受參數。  
  
 如果從 DLL 呼叫 `_onexit`，以 `_onexit` 註冊的常式會在使用 DLL_PROCESS_DETACH 呼叫 `DllMain` 之後於 DLL 卸載時執行。  
  
 `_onexit` 是 Microsoft 擴充功能。 針對 ANSI 可攜性，請使用 [atexit](../../c-runtime-library/reference/atexit.md)。 `_onexit_m` 版本的函式適用於混合模式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_onexit`|\<stdlib.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="output"></a>輸出  
  
```  
This is executed first.  
This is executed next.  
```  
  
## <a name="see-also"></a>請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [__dllonexit](../../c-runtime-library/dllonexit.md)