---
title: "casinh、casinhf、casinhl | Microsoft Docs"
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
- casinh
- casinhl
- casinhf
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
- casinh
- casinhf
- casinhl
- complex/casinh
- complex/casinhf
- complex/casinhl
dev_langs: C++
helpviewer_keywords:
- casinh function
- casinhf function
- casinhl function
ms.assetid: bd18340b-21dd-4c86-a14e-e8e15dd97e3b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2cc04c398bc9be13664a91e59a36f7e39fade6db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="casinh-casinhf-casinhl"></a>casinh、casinhf、casinhl
擷取與分支剪下間隔外部的複數的反雙曲正弦 [-i + 我] 軸虛數。  
  
## <a name="syntax"></a>語法  
  
```  
_Dcomplex casinh(   
   _Dcomplex z   
);  
_Fcomplex casinh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex casinh(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex casinhf(   
   _Fcomplex z   
);  
_Lcomplex casinhl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>參數  
 `z`  
 代表角度的複數 (弧度)。  
  
## <a name="return-value"></a>傳回值  
 `z` 的反雙曲正弦值 (弧度)。 結果是在實際的軸和間隔中未繫結 [-iπ/2 + iπ/2] 的虛數座標軸。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `casinh` 和 `_Fcomplex` 值的 `_Lcomplex` 的多載。 在 C 程式中， `casinh` 會一律採用及傳回 `_Dcomplex` 。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|C 標頭|C++ 標頭|  
|-------------|--------------|------------------|  
|`casinh`,               `casinhf`, `casinhl`|\<complex.h>|\<ccomplex>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh、catanhf、catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh、ctanhf、ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan、catanf、catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh、csinhf、csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [ccosh、ccoshf、ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh、cacoshf、cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos、cacosf、cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan、ctanf、ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin、csinf、csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin、casinf、casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos、ccosf、ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt、csqrtf、csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)