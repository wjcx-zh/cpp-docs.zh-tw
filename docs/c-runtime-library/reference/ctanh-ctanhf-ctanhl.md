---
title: "ctanh、ctanhf、ctanhl | Microsoft Docs"
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
- ctanh
- ctahf
- ctahl
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
- ctanh
- ctanhf
- ctanhl
- complex/ctanh
- complex/ctanhf
- complex/ctanhl
dev_langs:
- C++
helpviewer_keywords:
- ctanh function
- ctanhl function
- ctanhf function
ms.assetid: 807f2cd1-8740-4988-afff-5911c346385b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae85904fac6b68dfc04559dfe94c640477d12fb2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ctanh-ctanhf-ctanhl"></a>ctanh、ctanhf、ctanhl
計算複數的複雜雙曲正切值。  
  
## <a name="syntax"></a>語法  
  
```  
_Dcomplex ctanh(   
   _Dcomplex z   
);  
_Fcomplex ctanh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex ctanh(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex ctanhf(   
   _Fcomplex z   
);  
_Lcomplex ctanhl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>參數  
 `z`  
 代表角度的複數 (弧度)。  
  
## <a name="return-value"></a>傳回值  
 `z` 的複雜雙曲正切值。  
  
|輸入|SEH 例外狀況|`_matherr` 例外狀況|  
|-----------|-------------------|--------------------------|  
|± ∞、QNAN、IND|無|_DOMAIN|  
|± ∞ （tan、 tanf）|無效|_DOMAIN|  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `ctanh` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `ctanh` 會一律採用及傳回 `_Dcomplex` 。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|C 標頭|C++ 標頭|  
|-------------|--------------|------------------|  
|`ctanh`,               `ctanhf`, `ctanhl`|\<complex.h>|\<ccomplex>|  
  
 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh、catanhf、catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [catan、catanf、catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh、csinhf、csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh、casinhf、casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh、ccoshf、ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh、cacoshf、cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos、cacosf、cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan、ctanf、ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin、csinf、csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin、casinf、casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos、ccosf、ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt、csqrtf、csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)