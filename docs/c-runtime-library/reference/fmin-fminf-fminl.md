---
title: "fmin、 fminf、 fminl |Microsoft 文件"
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
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
caps.latest.revision: 5
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
translationtype: Machine Translation
ms.sourcegitcommit: 8953e3bd81158ce183e1abb5dfa969164c1f9ced
ms.openlocfilehash: b7fd6a2b91c1bc7cd973d2ac60f2d6fc39d322bb
ms.lasthandoff: 02/24/2017

---
# <a name="fmin-fminf-fminl"></a>fmin、fminf、fminl
決定兩個指定值的較小者。  
  
## <a name="syntax"></a>語法  
  
```  
double fmin(  
   double x,   
   double y  
);  
  
float fmin(  
   float x,   
   float y  
); //C++ only  
  
long double fmin(  
   long double x,   
   long double y  
); //C++ only  
  
float fminf(  
   float x,   
   float y  
);  
  
long double fminl(  
   long double x,   
   long double y  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 要比較的第一個值。  
  
 `y`  
 要比較的第二個值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `x` 或 `y` 的較小者。  
  
|輸入|結果|  
|-----------|------------|  
|`x` 是 NaN|`y`|  
|`y` 是 NaN|`x`|  
|`x` 和 `y` 是 NaN|NaN|  
  
 此函式不會叫用 [_matherr](../../c-runtime-library/reference/matherr.md)、不會導致任何浮點例外狀況，或不會變更 `errno` 的值。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回浮點和長雙精度浮點數類型的 `fmin` 多載。 在 C 程式中，`fmin` 一律採用及傳回雙精度浮點數。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`fmin`, `fminf`, `fminl`|C：\<math.h><br />C++：\<math.h> 或 \<cmath>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)  
 [fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)  
