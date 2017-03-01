---
title: "exp、expf | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- expf
- exp
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
- _expl
- expf
- exp
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- expf function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 4f6fb2d2dc585633915587ff7b6e5cfbd69c4deb
ms.lasthandoff: 02/24/2017

---
# <a name="exp-expf"></a>exp、expf
計算指數。  
  
## <a name="syntax"></a>語法  
  
```  
double exp(   
   double x  
);  
float exp(  
   float x  
);  // C++ only  
long double exp(  
   long double x  
);  // C++ only  
float expf(   
   float x  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 浮點值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，`exp` 函式會傳回浮點參數的指數值 `x`。 亦即，結果是以 e 為底的 `x` 次方，其中 e 是自然對數的底數。 溢位時函式傳回 INF (無限)，反向溢位時 `exp` 傳回 0。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|-----------|-------------------|-----------------------|  
|± QNAN、IND|無|_DOMAIN|  
|± ∞|INVALID|_DOMAIN|  
|x ≥ 7.097827e+002|INEXACT+OVERFLOW|OVERFLOW|  
|X ≤ -7.083964e+002|INEXACT+UNDERFLOW|UNDERFLOW|  
  
 `exp` 有使用 Streaming SIMD Extensions 2 (SSE2) 的實作。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## <a name="remarks"></a>備註  
 C++ 允許多載，因此您可以呼叫 `exp` 多載。 在 C 程式中，`exp` 一律採用及傳回雙精度浮點數。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`exp`, `expf`|\<math.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_exp.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.302585093, y;  
  
   y = exp( x );  
   printf( "exp( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
exp( 2.302585 ) = 10.000000  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 [System::Math::Exp](https://msdn.microsoft.com/en-us/library/system.math.exp.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [_CIexp](../../c-runtime-library/ciexp.md)
