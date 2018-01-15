---
title: "fmod、fmodf | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fmod
- fmodf
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
- fmod
- _fmodl
- fmodf
dev_langs: C++
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 53c191639222df29d8a1101d4ebfa7ea44377f48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fmod-fmodf"></a>fmod、fmodf
計算浮點餘數。  
  
## <a name="syntax"></a>語法  
  
```  
double fmod(   
   double x,  
   double y   
);  
float fmod(  
   float x,  
   float y   
);  // C++ only  
long double fmod(  
   long double x,  
   long double y  
);  // C++ only  
float fmodf(   
   float x,  
   float y   
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`, `y`  
 浮點值。  
  
## <a name="return-value"></a>傳回值  
 `fmod` 會傳回 `x` / `y` 的浮點餘數。 如果 `y` 的值為 0.0，則 `fmod` 會傳回無訊息 NaN。 如需透過 `printf` 系列表示無訊息 NaN 的資訊，請參閱 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## <a name="remarks"></a>備註  
 如果 `x` = `i` `*` `y` + `f`，`fmod` 函式會計算 `x` / `y` 的浮點餘數 `f`，其中 `i` 是整數、`f` 的正負號與 `x` 相同，而且 `f` 的絕對值小於 `y` 的絕對值。  
  
 C++ 允許多載，因此您可以呼叫 `fmod` 的多載。 在 C 程式中，`fmod` 一律會採用兩個雙精度浮點數並傳回一個雙精度浮點數。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`fmod`, `fmodf`|\<math.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_fmod.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = fmod( w, x );  
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );  
}  
```  
  
```Output  
The remainder of -10.00 / 3.00 is -1.000000  
```  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [fabs、fabsf、fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [_CIfmod](../../c-runtime-library/cifmod.md)