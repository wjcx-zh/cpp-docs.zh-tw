---
title: "fdim、fdimf、fdiml | Microsoft Docs"
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
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs: C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ecf0b0590942aad133cb7b8f478200525e4f4519
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fdim-fdimf-fdiml"></a>fdim、fdimf、fdiml
判斷第一個和第二個值之間的正差。  
  
## <a name="syntax"></a>語法  
  
```  
double fdim(  
   double x,   
   double y  
);  
  
float fdim(  
   float x,   
   float y  
); //C++ only  
  
long double fdim(  
   long double x,   
   long double y  
); //C++ only  
  
float fdimf(  
   float x,   
   float y  
);  
  
long double fdiml(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `x`  
 第一個值。  
  
 [輸入] `y`  
 第二個值。  
  
## <a name="return-value"></a>傳回值  
 傳回 `x` 與 `y` 之間的正差：  
  
|傳回值|情節|  
|------------------|--------------|  
|x-y|如果 x > y|  
|0|如果 x <= y|  
  
 否則，可能會傳回下列一項錯誤：  
  
|問題|Return|  
|-----------|------------|  
|溢位範圍錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|  
|反向溢位範圍錯誤|正確的值 (四捨五入後)|  
|`x` 或 `y` 是 NaN|NaN|  
  
 依 [_matherr](../../c-runtime-library/reference/matherr.md) 中的指定回報錯誤。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回浮點和長雙精度浮點數類型的 `fdim` 多載。 在 C 程式中，`fdim` 一律採用及傳回雙精度浮點數。  
  
 除了 NaN 處理中，此函式相當於`fmax(x - y, 0)`。  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`fdim`, `fdimf`, `fdiml`|\<math.h>|\<cmath>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmax、fmaxf、fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [abs、labs、llabs、_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)