---
title: "fma、fmaf、fmal | Microsoft Docs"
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
- fma
- fmaf
- fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
dev_langs:
- C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
caps.latest.revision: 10
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
ms.openlocfilehash: 59238cf511be936b0d882c2f00320ee7422904e0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="fma-fmaf-fmal"></a>fma、fmaf、fmal
將兩個值相乘，並加上第三個值，然後對結果進行四捨五入，而且不會因中值四捨五入而遺失任何精確度。  
  
## <a name="syntax"></a>語法  
  
```  
double fma(  
   double x,   
   double y,   
   double z  
);  
  
float fma(  
   float  x,   
   float  y,   
   float z  
); //C++ only  
  
long double fma(  
   long double  x,   
   long double  y,   
   long double z  
); //C++ only  
  
float fmaf(  
   float  x,   
   float  y,   
   float z  
);  
  
long double fmal(  
   long double  x,   
   long double  y,   
   long double z  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 [in] `x`  
 要相乘的第一個值。  
  
 [in] `y`  
 要相乘的第二個值。  
  
 [in] `z`  
 要加入的值。  
  
## <a name="return-value"></a>傳回值  
 傳回 `(x * y) + z`。 傳回值接著會使用目前的四捨五入格式來進行四捨五入。  
  
 否則，可能會傳回下列其中一個值：  
  
|問題|返回|  
|-----------|------------|  
|`x` = INFINITY、`y` = 0 或<br /><br /> `x` = 0、`y` = INFINITY|NaN|  
|`x` 或 `y` = 完全相同 ± INFINITY、`z` = INFINITY (含相反的正負號)|NaN|  
|`x` 或 `y` = NaN|NaN|  
|非 (`x` = 0、`y`= 無限制) 和 `z` = NaN<br /><br /> 非 (`x`=無限制、`y`=0) 和 `z` = NaN|NaN|  
|溢位範圍錯誤|±HUGE_VAL、±HUGE_VALF 或 ±HUGE_VALL|  
|反向溢位範圍錯誤|四捨五入後的正確值。|  
  
 依 [_matherr](../../c-runtime-library/reference/matherr.md) 的指定回報錯誤。  
  
## <a name="remarks"></a>備註  
 因為 c + + 允許多載，所以您可以呼叫的多載`fma`採用並傳回**float**和**長雙精度**型別。 在 C 程式中，`fma`一律採用並傳回**double**。  
  
 此函式會計算值，就像它採用無限精確度，然後將最終結果進行四捨五入。  
  
## <a name="requirements"></a>需求  
  
|函式|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`fma`, `fmaf`, `fmal`|\<math.h>|\<cmath>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [remainder、remainderf、remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)   
 [remquo、remquof、remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)
