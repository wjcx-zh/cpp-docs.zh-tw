---
title: "catanh、catanhf、catanhl | Microsoft Docs"
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
- catanh
- catanhf
- catanhl
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
- catanh
- catanhf
- catanhl
- complex/catanh
- complex/catanhf
- complex/catanhl
dev_langs:
- C++
helpviewer_keywords:
- catanh function
- catanhf function
- catanhl function
ms.assetid: 1b6021cb-647a-41b4-9d7f-919cc8b57b86
caps.latest.revision: 10
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: c70314e30419f6315fc1c3afe84e8e9fc104d728
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="catanh-catanhf-catanhl"></a>catanh、catanhf、catanhl
擷取與實際的軸間隔 [-1; + 1] 以外的分支剪下複數的反雙曲正切。  
  
## <a name="syntax"></a>語法  
  
```  
_Dcomplex catanh(   
   _Dcomplex z   
);  
_Fcomplex catanh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex catanh(   
   _Lcomplex z   
);  //  C++ only  
_Fcomplex catanhf(   
   _Fcomplex z   
);  
_Lcomplex catanhl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>參數  
 `z`  
 代表角度的複數 (弧度)。  
  
## <a name="return-value"></a>傳回值  
 `z` 的反雙曲正切值 (弧度)。 結果是在實際的軸和間隔中未繫結 [-iπ/2; + iπ/2] 的虛數座標軸。 如果 `z` 落在間隔 [-1, +1] 外部，則會發生網域錯誤。 如果 `z` 是 -1 或 +1，則會發生極錯誤。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `catanh` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `catanh` 會一律採用及傳回 `_Dcomplex` 。  
  
## <a name="requirements"></a>需求  
  
|常式|C 標頭|C++ 標頭|  
|-------------|--------------|------------------|  
|`catanh`,               `catanhf`, `catanhl`|\<complex.h>|\<ccomplex>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [ctanh、ctanhf、ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
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
