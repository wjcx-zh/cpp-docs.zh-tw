---
title: "erf、erff、erfl、erfc、erfcf、erfcl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
dev_langs: C++
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 54256f68263ea966466c9c038f429ab4a73fc868
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf、erff、erfl、erfc、erfcf、erfcl
計算值的錯誤函式或補充錯誤函式。  
  
## <a name="syntax"></a>語法  
  
```  
double erf(  
   double x  
);  
float erf(  
   float x  
); // C++ only  
long double erf(  
   long double x  
); // C++ only  
float erff(  
   float x  
);  
long double erfl(  
   long double x  
);  
double erfc(  
   double x  
);  
float erfc(  
   float x  
); // C++ only  
long double erfc(  
   long double x  
); // C++ only  
float erfcf(  
   float x  
);  
long double erfcl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 浮點值。  
  
## <a name="return-value"></a>傳回值  
 `erf` 函式會傳回 `x` 的高斯錯誤函式。 `erfc` 函式會傳回 `x` 的補充高斯錯誤函式。  
  
## <a name="remarks"></a>備註  
 `erf` 函式會計算 x 的高斯錯誤函式，其定義為：  
  
 ![x 的誤差函式](../../c-runtime-library/reference/media/crt_erf_formula.PNG "CRT_erf_formula")  
  
 補充高斯錯誤函式定義為 1-erf （x)。 `erf` 函式會傳回範圍 -1.0 到 1.0 的值。 不會傳回錯誤。 `erfc` 函式會傳回範圍 0 到 2 的值。 若 `x` 對於 `erfc` 而言過大，會將 `errno` 變數設為 `ERANGE`。  
  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `erf` 和 `erfc` 類型的 `float` 和 `long double` 的多載。 在 C 程式中，`erf` 和 `erfc` 會一律採用並傳回 `double`。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`erf`, `erff`, `erfl`, `erfc`, `erfcf`, `erfcl`|\<math.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)