---
title: "cos、cosf、cosl、cosh、coshf、coshl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- coshl
- cosh
- cos
- cosl
- cosf
- coshf
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
- coshl
- cos
- cosf
- cosh
- cosl
- coshf
dev_langs: C++
helpviewer_keywords:
- cosines
- cosl function
- calculating cosine
- cosf function
- cos function
- cosh function
- coshf function
- trigonometric functions
- cosines, calculating
- coshl function
- hyperbolic functions
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e06a929148da03e59edff6f0630cd60841e912e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cos-cosf-cosl-cosh-coshf-coshl"></a>cos、cosf、cosl、cosh、coshf、coshl
計算餘弦值 (`cos`、`cosf` 或 `cosl`) 或雙曲餘弦值 (`cosh`、`coshf` 或 `coshl`)。  
  
## <a name="syntax"></a>語法  
  
```  
double cos(   
   double x   
);  
float cos(  
   float x   
);  // C++ only  
long double cos(  
   long double x  
);  // C++ only  
float cosf(   
   float x   
);  
long double cosl(  
   long double x  
);  
double cosh(   
   double x   
);  
float cosh(  
   float x   
);  // C++ only  
long double cosh(  
   long double x  
);  // C++ only  
float coshf(  
   float x   
);  
long double coshl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 角度 (弧度)。  
  
## <a name="return-value"></a>傳回值  
 `x` 的餘弦值或雙曲餘弦值。 如果`x`大於或等於 263，或小於或等於-263，遺失精確度結果中的呼叫`cos`， `cosf`，或`cosl`，就會發生。  
  
 根據預設，如果 `cosh`、`coshf` 或 `coshl` 呼叫中的結果太大，則此函式會傳回 `HUGE_VAL`，並將 `errno` 設為 `ERANGE`。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|無|`_DOMAIN`|  
|± ∞  (`cosf`, `cos`, `cosl`)|`INVALID`|`_DOMAIN`|  
|x ≥ 7.104760e+002 (`cosh`、`coshf`、`coshl`)|`INEXACT`+`OVERFLOW`|`OVERFLOW`|  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `float` 或 `long double` 值之 `cos` 和 `cosh` 的多載。 在 C 程式中，`cos` 和 `cosh` 會一律採用並傳回 `double`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`cos`, `cosh`, `cosf`, `coshf`, `cosl`, `coshl`|\<math.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md) 中的範例。  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_CIcos](../../c-runtime-library/cicos.md)