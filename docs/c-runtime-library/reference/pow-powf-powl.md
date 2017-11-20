---
title: "pow、powf、powl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
dev_langs: C++
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43156626c92160003a5ef0d5364b5a006df5141e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="pow-powf-powl"></a>pow、powf、powl
計算自乘至 `y` 的乘冪的 `x`。  
  
## <a name="syntax"></a>語法  
  
```  
double pow(  
   double x,  
   double y   
);  
double pow(  
   double x,  
   int y  
);  // C++ only  
float pow(  
   float x,  
   float y   
);  // C++ only  
float pow(  
   float x,  
   int y  
);  // C++ only  
long double pow(  
   long double x,  
   long double y  
);  // C++ only  
long double pow(  
   long double x,  
   int y  
);  // C++ only  
float powf(  
   float x,  
   float y   
);  
long double powl(  
   long double x,  
   long double y  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 底數。  
  
 `y`  
 指數。  
  
## <a name="return-value"></a>傳回值  
 傳回 `x`<sup>y</sup> 的值。 溢位或反向溢位時不會列印錯誤訊息。  
  
|x 和 y 的值|pow 的傳回值|  
|-----------------------|-------------------------|  
|`x` \< > 0 且 `y` = 0.0|1|  
|`x` = 0.0 且 `y` = 0.0|1|  
|`x` = 0.0 且 `y` < 0|INF|  
  
## <a name="remarks"></a>備註  
 `pow` 無法辨識大於 2<sup>64</sup> 的整數浮點值 (例如 `1.0E100`)。  
  
 `pow` 具有使用 Streaming SIMD Extensions 2 (SSE2) 的實作。 如需使用 SSE2 實作的相關資訊和限制，請參閱 [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
 因為 C++ 允許多載，所以您可以呼叫 `pow` 的各種多載。 在 C 程式中，`pow` 會一律採用兩個雙精確度值並傳回一個雙精確度值。  
  
 `pow(int, int)` 已無法使用。 如果您使用此多載，編譯器可能會發出 C2668。 若要避免這個問題，請將第一個參數轉換為 `double`、`float` 或 `long double`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`pow`, `powf`, `powl`|\<math.h>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_pow.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.0, y = 3.0, z;  
  
   z = pow( x, y );  
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
2.0 to the power of 3.0 is 8.0  
```  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [exp、 expf，總管](../../c-runtime-library/reference/exp-expf.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [sqrt、sqrtf、sqrtl](../../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)   
 [_CIpow](../../c-runtime-library/cipow.md)