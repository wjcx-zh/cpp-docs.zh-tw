---
title: "nearbyint、nearbyintf、nearbyintl1 | Microsoft Docs"
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
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
dev_langs: C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d95f92d15dcf4b8baf84b762b994bdb52930346d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint、nearbyintf、nearbyintl
將指定的浮點值四捨五入成整數，並以浮點數格式傳回該值。  
  
## <a name="syntax"></a>語法  
  
```  
double nearbyint(  
   double x  
);  
  
float nearbyint(  
   float x  
); //C++ only  
  
long double nearbyint(  
   long double x  
); //C++ only  
  
float nearbyintf(  
   float x  
);  
  
long double nearbyintl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `x`  
 要捨入的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回使用 fegetround 所定義之目前進位格式四捨五入成最接近整數的 `x`。 否則，此函式可能會傳回下列其中一個值：  
  
|問題|Return|  
|-----------|------------|  
|`x`= ±INFINITY|±INFINITY，未修改|  
|`x` = ±0|±0，未修改|  
|`x` = NAN|NaN|  
  
 錯誤不會透過 [_matherr](../../c-runtime-library/reference/matherr.md) 回報；具體來說，此函式不會回報任何 FE_INEXACT 例外狀況。  
  
## <a name="remarks"></a>備註  
 此函式和 `rint` 之間的主要差異，即在於此函式不會引發不精確的浮點例外狀況。  
  
 因為最大浮點值是精確的整數，所以此函式自身永遠不會溢位；相反地，根據您使用的函式版本，輸出可能會造成傳回值溢位。  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`nearbyint`,                `nearbyintf`,  `nearbyintl`|\<math.h>|\<cmath>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)