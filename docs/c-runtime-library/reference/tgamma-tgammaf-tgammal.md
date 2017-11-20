---
title: "tgamma、tgammaf、tgammal | Microsoft Docs"
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
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
dev_langs: C++
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 24c4cc90ed77a57ad053f5608ad5eaf2d1ed62f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma、tgammaf、tgammal
判斷指定值的 gamma 函式。  
  
## <a name="syntax"></a>語法  
  
```  
double tgamma(  
   double x  
);  
  
float tgamma(  
   float x  
); //C++ only  
  
long double tgamma(  
   long double x  
); //C++ only  
  
float tgammaf(  
   float x  
);  
  
long double tgammal(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 [in] `x`  
 要尋找其 gamma 的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `x` 的 gamma。  
  
 如果 `x` 的量級對資料類型而言太大或太小，可能發生範圍錯誤。 如果 `x` <=0，可能發生網域錯誤或範圍錯誤。  
  
|問題|返回|  
|-----------|------------|  
|x = ±0|±INFINITY|  
|x = 負整數|NaN|  
|x =  -INFINITY|NaN|  
|x = +INFINITY|+INFINITY|  
|x = NaN|NaN|  
|網域錯誤|NaN|  
|極錯誤|±HUGE_VAL、±HUGE_VALF 或 ±HUGE_VALL|  
|溢位範圍錯誤|±HUGE_VAL、±HUGE_VALF 或 ±HUGE_VALL|  
|反向溢位範圍錯誤|正確的值 (四捨五入後)。|  
  
 錯誤依 [_matherr](../../c-runtime-library/reference/matherr.md) 中的指定回報。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回浮點和長雙精度浮點數類型的 tgamma 多載。 在 C 程式中，tgamma 會一律採用並傳回雙精度浮點數。  
  
 如果 x 為自然數，此函式會傳回 (x-1) 階乘。  
  
## <a name="requirements"></a>需求  
  
|函式|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`tgamma`,                `tgammaf`,  `tgammal`|\<math.h>|\<cmath>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [lgamma、lgammaf、lgammal](../../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)