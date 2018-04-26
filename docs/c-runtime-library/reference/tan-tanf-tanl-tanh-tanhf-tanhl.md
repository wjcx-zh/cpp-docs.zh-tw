---
title: tan、tanf、tanl、tanh、tanhf、tanhl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- tanhf
- tanh
- tan
- tanhl
- tanf
- tanl
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
- tanh
- tan
- _tanl
- tanl
- _tanhl
- tanf
- tanhf
- tanhl
dev_langs:
- C++
helpviewer_keywords:
- tanl function
- tanhl function
- _tanl function
- _tanhl function
- tan function
- calculating tangents
- tangent
- tanh function
- tanhf function
- tanf function
- trigonometric functions
- hyperbolic functions
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c3391d07e78ba177a3ce31abb26bd5b6ef0449c
ms.sourcegitcommit: 9a3a3d59176043ae60584482c2572c07f757b320
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="tan-tanf-tanl-tanh-tanhf-tanhl"></a>tan、tanf、tanl、tanh、tanhf、tanhl
計算正切 (`tan`、`tanf` 或 `tanl`) 或雙曲正切 (`tanh`、`tanhf` 或 `tanhl`)。  
  
## <a name="syntax"></a>語法  
  
```  
double tan(  
   double x   
);  
float tan(  
   float x   
);  // C++ only  
long double tan(  
   long double x  
);  // C++ only  
float tanf(  
   float x   
);  
long double tanl(  
   long double x  
);  
double tanh(  
   double x   
);  
float tanh(  
   float x   
);  // C++ only  
long double tanh(  
   long double x  
);  // C++ only  
float tanhf(  
   float x   
);  
long double tanhl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 角度 (弧度)。  
  
## <a name="return-value"></a>傳回值  
 `tan` 函式會傳回 `x` 的正切。 如果`x`是大於或等於 263，或小於或等於-263，就會發生遺失精確度結果。  
  
 `tanh` 函式會傳回 `x` 的雙曲正切。 不會傳回錯誤。  
  
|輸入|SEH 例外狀況|`Matherr` 例外狀況|  
|-----------|-------------------|-------------------------|  
|± QNAN、IND|無|_DOMAIN|  
|± ∞  (`tan`, `tanf`)|`INVALID`|_DOMAIN|  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫接受並傳回 `float` 或 `long double` 值之 `tan` 和 `tanh` 的多載。 在 C 程式中，`tan` 和 `tanh` 一律會接受並傳回 `double`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`tan`, `tanf`, `tanl`, `tanh`, `tanhf`, `tanhl`|\<math.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_tan.c  
// This program displays the tangent of pi / 4  
// and the hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tan( pi / 4 );  
   y = tanh( x );  
   printf( "tan( %f ) = %f\n", pi/4, x );  
   printf( "tanh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
tan( 0.785398 ) = 1.000000  
tanh( 1.000000 ) = 0.761594  
```  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [_CItan](../../c-runtime-library/citan.md)