---
title: "round、roundf、roundl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- round
- roundl
- roundf
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
- roundf
- roundl
- round
dev_langs: C++
helpviewer_keywords:
- roundl function
- round function
- roundf function
ms.assetid: 6be90877-193c-4b80-a32b-c3eca33f9c6f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0209e85b6846136a97a2c9fece459b6dc1ec4513
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="round-roundf-roundl"></a>round、roundf、roundl
將浮點值四捨五入為最接近的整數。  
  
## <a name="syntax"></a>語法  
  
```  
double round(   
   double x   
);  
float round(  
   float x  
);  // C++ only  
long double round(  
   long double x  
);  // C++ only  
float roundf(  
   float x  
);  
long double roundl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 要四捨五入的浮點值。  
  
## <a name="return-value"></a>傳回值  
 `round` 函式會傳回表示 `x` 的最接近整數的浮點值。 不論浮點四捨五入模式的設定為何，進行四捨五入時，中間值都會背離零。 不會傳回錯誤。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|無|`_DOMAIN`|  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `round` 和 `float` 值的 `long double` 的多載。 在 C 程式中，`round` 會一律採用並傳回 `double`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`round`, `roundf`, `roundl`|\<math.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_round.c  
// Build with: cl /W3 /Tc crt_round.c  
// This example displays the rounded results of  
// the floating-point values 2.499999, -2.499999,   
// 2.8, -2.8, 2.5 and -2.5.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.499999;  
   float y = 2.8f;  
   long double z = 2.5;  
  
   printf("round(%f) is %.0f\n", x, round(x));  
   printf("round(%f) is %.0f\n", -x, round(-x));  
   printf("roundf(%f) is %.0f\n", y, roundf(y));  
   printf("roundf(%f) is %.0f\n", -y, roundf(-y));  
   printf("roundl(%Lf) is %.0Lf\n", z, roundl(z));  
   printf("roundl(%Lf) is %.0Lf\n", -z, roundl(-z));  
}  
```  
  
```Output  
round(2.499999) is 2  
round(-2.499999) is -2  
roundf(2.800000) is 3  
roundf(-2.800000) is -3  
roundl(2.500000) is 3  
roundl(-2.500000) is -3  
```  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [lrint、lrintf、lrintl、llrint、llrintf、llrintl](http://msdn.microsoft.com/en-us/312fd869-a9c0-4107-bb23-ab8299d04385)   
 [lround、lroundf、lroundl、llround、llroundf、llroundl](../../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)   
 [nearbyint、nearbyintf、nearbyintl](http://msdn.microsoft.com/en-us/15111e73-331d-41d1-81b7-3e10df894848)   
 [rint、rintf、rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)