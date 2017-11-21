---
title: "remainder、remainderf、remainder | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
dev_langs: C++
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 78ba9803ab4eddd862d407fa79f7fa99fc0b565c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="remainder-remainderf-remainderl"></a>remainder、remainderf、remainderl
計算兩個浮點值商數的餘數，四捨五入為最接近的整數值。  
  
## <a name="syntax"></a>語法  
  
```  
double remainder(   
   double numer,  
   double denom  
);  
float remainder(   
   float numer,  
   float denom  
); /* C++ only */  
long double remainder(   
   long double numer,  
   long double denom  
); /* C++ only */  
float remainderf(   
   float numer,  
   float denom  
);  
long double remainderl(   
   long double numer,  
   long double denom  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## <a name="return-value"></a>傳回值  
 `x` / `y` 的浮點餘數。 如果 `y` 的值為 0.0，則 `remainder` 會傳回無訊息 NaN。 如需透過 `printf` 系列表示無訊息 NaN 的資訊，請參閱 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## <a name="remarks"></a>備註  
 `remainder` 函式會計算 `x` / `y` 之 `r` 的浮點數餘數，使得 `x` = `n` * `y` + `r`，其中 `n` 是值最接近 `x` / `y` 的整數，且每當 &#124; `n` - `x` / `y` &#124; = 1/2 時，`n` 是偶數。 當 `r` = 0 時，`r` 的正負號與 `x` 相同。  
  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `remainder` 或 `float` 值的 `long double` 的多載。 在 C 程式中，`remainder` 一律會採用兩個雙精度浮點數並傳回一個雙精度浮點數。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`remainder`, `remainderf`, `remainderl`|\<math.h>|  
  
 如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```C  
// crt_remainder.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = remainder(w, x);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
}  
```  
  
```Output  
The remainder of -10.00 / 3.00 is -1.000000  
```  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remquo、remquof、remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)