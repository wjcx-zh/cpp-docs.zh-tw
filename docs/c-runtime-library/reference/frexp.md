---
title: frexp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- frexp
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- frexp
- _frexpl
dev_langs:
- C++
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02eab6e7912a69a6189568d9a5530ace88d8430b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="frexp"></a>frexp
取得浮點數的尾數和指數。  
  
## <a name="syntax"></a>語法  
  
```  
double frexp(  
   double x,  
   int *expptr   
);  
float frexp(  
   float x,  
   int * expptr  
);  // C++ only  
long double frexp(  
   long double x,  
   int * expptr  
);  // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 浮點值。  
  
 `expptr`  
 預存整數指數的指標。  
  
## <a name="return-value"></a>傳回值  
 `frexp` 會傳回尾數。 如果 `x` 是 0，則此函式會針對尾數和指數傳回 0。 如果 `expptr` 為 `NULL`，則會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 0。  
  
## <a name="remarks"></a>備註  
 `frexp`細分的浮點值的函式 (`x`) 到尾數 (`m`) 和指數 (`n`)，這類數值的絕對值`m`大於或等於 0.5 且小於 1.0 和`x` =  `m`* 2<sup>n</sup>。 整數指數 `n` 儲存在 `expptr` 所指向的位置。  
  
 C++ 允許多載，因此您可以呼叫 `frexp` 的多載。 在 C 程式中，`frexp` 一律會採用雙精度浮點和整收，並傳回雙精度浮點。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`frexp`|\<math.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_frexp.c  
// This program calculates frexp( 16.4, &n )  
// then displays y and n.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y;  
   int n;  
  
   x = 16.4;  
   y = frexp( x, &n );  
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );  
}  
```  
  
```Output  
frexp( 16.400000, &n ) = 0.512500, n = 5  
```  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)   
 [modf、modff、modfl](../../c-runtime-library/reference/modf-modff-modfl.md)