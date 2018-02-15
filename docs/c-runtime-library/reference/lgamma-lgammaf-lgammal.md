---
title: "lgamma、 lgammaf、 lgammal | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- lgamma
- lgammaf
- lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
dev_langs:
- C++
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7ef4a64252342484a1c6aa68722013f1e6bffdf
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma、lgammaf、lgammal
判斷指定值之 gamma 函式絕對值的自然對數。  
  
## <a name="syntax"></a>語法  
  
```  
double lgamma(  
   double x  
);  
  
float lgamma(  
   float x  
); //C++ only  
  
long double lgamma(  
   long double x  
); //C++ only  
  
float lgammaf(  
   float x  
);  
  
long double lgammal(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `x`  
 要計算的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `x.` 之 gamma 函式絕對值的自然對數  
  
|問題|Return|  
|-----------|------------|  
|`x` = NaN|NaN|  
|`x` = ±0|+INFINITY|  
|`x`= 非負值整數|+INFINITY|  
|±INFINITY|+INFINITY|  
|極錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|  
|溢位範圍錯誤|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|  
  
 錯誤依 [_matherr](../../c-runtime-library/reference/matherr.md) 中的指定回報。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回浮點和長雙精度浮點數類型的 `lgamma` 多載。 在 C 程式中，`lgamma` 一律採用並傳回雙精度浮點。  
  
 如果 x 為有理數，此函式會傳回 (`x`-1) 階乘的對數。  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`lgamma`,                `lgammaf`,  `lgammal`|\<math.h>|\<cmath>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [tgamma、tgammaf、tgammal](../../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)