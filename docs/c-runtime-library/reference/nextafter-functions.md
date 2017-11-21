---
title: "nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
dev_langs: C++
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3dad9078ba4c683b4d29d366943559ad8228cb31
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl
傳回下一個所能顯示的浮點值。  
  
## <a name="syntax"></a>語法  
  
```  
double nextafter(  
   double x,  
   double y   
);  
  
float nextafter(  
   float x,  
   float y   
); /* C++ only, requires <cmath> */  
  
long double nextafter(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nextafterf(  
   float x,  
   float y   
);   
  
long double nextafterl(  
   long double x,  
   long double y   
);  
  
double _nextafter(  
   double x,  
   double y   
);  
  
float _nextafterf(  
   float x,  
   float y   
); /* x64 only */  
  
double nexttoward(  
   double x,  
   long double y   
);  
  
float nexttoward(  
   float x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
long double nexttoward(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nexttowardf(  
   float x,  
   long double y   
);   
  
long double nexttowardl(  
   long double x,  
   long double y   
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 起始的浮點值。  
  
 `y`  
 要前往的浮點值。  
  
## <a name="return-value"></a>傳回值  
 傳回 `y` 方向中 `x` 之後下一個所能顯示且屬於傳回型別的浮點值。 如果 `x`=`y`，此函式會傳回轉換成傳回型別的 `y`，而不會觸發任何例外狀況。 如果 `x` 不等於 `y`，而且結果異常或為零，則會設定 FE_UNDERFLOW 和 FE_INEXACT 浮點例外狀況狀態，並傳回正確的結果。 如果 `x` 或 `y` 為 NAN，則傳回值是其中一個輸入 NAN。 如果 `x` 是有限值，但結果無限或無法在此類型中顯示，則會傳回正負號正確的無限大或 NAN、設定 FE_OVERFLOW 和 FE_INEXACT 浮點例外狀況狀態，並將 `errno` 設定為 ERANGE。  
  
## <a name="remarks"></a>備註  
 `nextafter` 和 `nexttoward` 函式系列相同，只不過 `y` 的參數類型不同。 如果 `x` 和 `y` 相等，傳回的值會是轉換成傳回型別的 `y`。  
  
 因為 C++ 允許多載，所以如果您包含 \<cmath>，您可以呼叫傳回 `float` 和 `long double` 類型之 `nextafter` 和 `nexttoward` 的多載。 在 C 程式中，`nextafter` 和 `nexttoward` 會一律傳回 `double`。  
  
 `_nextafter` 和 `_nextafterf` 函式為 Microsoft 特有。 `_nextafterf` 函式只適用於 x64 編譯時。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭 (C)|必要的標頭 (C++)|  
|-------------|---------------------------|-------------------------------|  
|`nextafter`, `nextafterf`, `nextafterl`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`|\<math.h>|\<math.h> 或 \<cmath>|  
|`_nextafter`|\<float.h>|\<float.h> 或 \<cfloat>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [isnan、_isnan、_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)