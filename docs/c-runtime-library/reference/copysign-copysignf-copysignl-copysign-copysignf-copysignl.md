---
title: "copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
dev_langs:
- C++
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 513ba53a63351b7239c0612103c41977e930eafa
ms.lasthandoff: 02/24/2017

---
# <a name="copysign-copysignf-copysignl-copysign-copysignf-copysignl"></a>copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl
傳回一個值，具有其中一個引數的大小和另一個引數的正負號。  
  
## <a name="syntax"></a>語法  
  
```  
double copysign(   
   double x,  
   double y   
);  
float copysign(   
   float x,  
   float y   
); // C++ only  
long double copysign(   
   long double x,  
   long double y   
); // C++ only  
float copysignf(   
   float x,  
   float y   
); // C++ only  
long double copysignl(   
   long double x,  
   long double y   
); // C++ only  
double _copysign(   
   double x,  
   double y   
);  
long double _copysignl(   
   long double x,  
   long double y   
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 傳回為結果大小的浮點值。  
  
 `y`  
 傳回為結果正負號的浮點值。  
  
 [浮點支援常式](../../c-runtime-library/floating-point-support.md)  
  
## <a name="return-value"></a>傳回值  
 `copysign` 函式會傳回合併 `x` 之大小和 `y`之正負號的浮點值。 不會傳回錯誤。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `copysign` 或 `float` 值的 `long double` 的多載。 在 C 程式中，`copysign` 會一律採用並傳回 `double`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_copysign`|\<float.h>|  
|`copysign`, `copysignf`, `copysignl`, `_copysignf``_copysignl`|\<math.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [fabs、fabsf、fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [_chgsign、_chgsignf、_chgsignl](../../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)
