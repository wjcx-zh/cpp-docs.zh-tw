---
title: "exp2、exp2f、exp2l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- exp2
- exp2f
- exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
dev_langs:
- C++
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 4c3e31359c096dddfc7d71dcd7887c405b9aa0af
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="exp2-exp2f-exp2l"></a>exp2、exp2f、exp2l
計算 2 的乘至指定的值。  
  
## <a name="syntax"></a>語法  
  
```  
double exp2(  
   double x  
);  
  
float exp2(  
   float x  
);  // C++ only  
  
long double exp2(  
   long double x  
); // C++ only  
  
float exp2f(  
   float x  
);  
  
long double exp2l(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `x`  
 指數值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回的基底 2 指數`x`，也就是 2<sup>x</sup>。 否則，它會傳回下列值之一︰  
  
|問題|返回|  
|-----------|------------|  
|`x` = ±0|1|  
|`x` = -INFINITY|+0|  
|`x` = +INFINITY|+INFINITY|  
|`x` = NaN|NaN|  
|溢位範圍錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|  
|反向溢位範圍錯誤|正確的結果，四捨五入之後|  
  
 錯誤依 [_matherr](../../c-runtime-library/reference/matherr.md) 中的指定回報。  
  
## <a name="remarks"></a>備註  
 因為 c + + 允許多載，所以您可以呼叫的多載`exp2`採用並傳回**float**和**長雙精度**型別。 在 C 程式中，`exp2`一律採用並傳回**double**。  
  
## <a name="requirements"></a>需求  
  
|常式|C 標頭|C++ 標頭|  
|-------------|--------------|------------------|  
|`exp`, `expf`, `expl`|\<math.h>|\<cmath>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [exp、 expf，總管](../../c-runtime-library/reference/exp-expf.md)   
 [log2、log2f、log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)
