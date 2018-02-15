---
title: "lround、lroundf、lroundl、llround、llroundf、llroundl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- llround
- llroundf
- llroundl
- lroundf
- lround
- lroundl
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
- lround
- lroundl
- llroundl
- llround
- lroundf
- llroundf
dev_langs:
- C++
helpviewer_keywords:
- lround function
- llroundl function
- llround function
- lroundf function
- llroundf function
- lroundl function
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2a3ec5e749823da6c49b7762334374292c8be50
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="lround-lroundf-lroundl-llround-llroundf-llroundl"></a>lround、lroundf、lroundl、llround、llroundf、llroundl
將浮點值四捨五入為最接近的整數。  
  
## <a name="syntax"></a>語法  
  
```  
long lround(   
   double x   
);  
long lround(  
   float x  
);  // C++ only  
long lround(  
   long double x  
);  // C++ only  
long lroundf(  
   float x  
);  
long lroundl(  
   long double x  
);  
long long llround(   
   double x   
);  
long long llround(  
   float x  
);  // C++ only  
long long llround(  
   long double x  
);  // C++ only  
long long llroundf(  
   float x  
);  
long long llroundl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 要四捨五入的浮點值。  
  
## <a name="return-value"></a>傳回值  
 `lround` 和 `llround` 函式會將最接近的 `long` 或 `long long` 整數傳回 `x`。 不論浮點進位模式設定為何，中間值都會背離零四捨五入。 不會傳回錯誤。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|-----------|-------------------|-----------------------|  
|± `QNAN`, `IND`|無|`_DOMAIN`|  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `float` 和 `long double` 值之 `lround` 或 `llround` 的多載。 在 C 程式中，`lround` 和 `llround` 會一律採用並傳回 `double`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`lround`, `lroundf`, `lroundl`, `llround`, `llroundf`, `llroundl`|\<math.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_lround.c  
// Build with: cl /W3 /Tc crt_lround.c  
// This example displays the rounded results of  
// the floating-point values 2.499999, -2.499999,   
// 2.8, -2.8, 3.5 and -3.5.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.499999;  
   float y = 2.8f;  
   long double z = 3.5;  
  
   printf("lround(%f) is %d\n", x, lround(x));  
   printf("lround(%f) is %d\n", -x, lround(-x));  
   printf("lroundf(%f) is %d\n", y, lroundf(y));  
   printf("lroundf(%f) is %d\n", -y, lroundf(-y));  
   printf("lroundl(%Lf) is %d\n", z, lroundl(z));  
   printf("lroundl(%Lf) is %d\n", -z, lroundl(-z));  
}  
```  
  
```Output  
lround(2.499999) is 2  
lround(-2.499999) is -2  
lroundf(2.800000) is 3  
lroundf(-2.800000) is -3  
lroundl(2.500000) is 4  
lroundl(-2.500000) is -4  
```  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [lrint、lrintf、lrintl、llrint、llrintf、llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)   
 [nearbyint、nearbyintf、nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)   
 [rint、rintf、rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)