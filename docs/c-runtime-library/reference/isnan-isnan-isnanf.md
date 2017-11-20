---
title: "isnan、_isnan、_isnanf | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
dev_langs: C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 982760deff4c5e2439c8743aa0de736a24faa02a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="isnan-isnan-isnanf"></a>isnan、_isnan、_isnanf
測試浮點值是否為非數字 (NAN)。  
  
## <a name="syntax"></a>語法  
  
```  
int isnan(  
   /* floating-point */ x   
); /* C-only macro */  
  
int _isnan(  
   double x   
);  
  
int _isnanf(  
   float x  
); /* x64 only */  
  
template <class T>  
bool isnan(  
   T x  
) throw(); /* C++ only */  
```  
  
#### <a name="parameters"></a>參數  
 *x*  
 要測試的浮點值。  
  
## <a name="return-value"></a>傳回值  
 在 C 中，如果引數 `x` 為 NAN，`isnan` 巨集和`_isnan` 和 `_isnanf` 函式會傳回非零值；否則會傳回 0。  
  
 在 C++ 中，如果引數 `x` 為 NAN，`isnan` 範本函式會傳回 `true`，否則會傳回`false`。  
  
## <a name="remarks"></a>備註  
 C 的 `isnan` 巨集和 `_isnan``_isnanf` 函式測試浮點值*x*，如果 *x* 不是數字 (NAN) 值，則傳回非零值。 浮點運算的結果無法以指定之類型的 IEEE-754 浮點數格式表示時，就會產生 NAN。 如需 NaN 如何在輸出中表示的資訊，請參閱 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
 當編譯為 C++ 時，`isnan` 巨集為未定義，並改為定義 `isnan` 範本函式。 它會傳回類型 `bool` 的值，而不是整數。  
  
 `_isnan` 和 `_isnanf` 函式為 Microsoft 特有。 `_isnanf` 函式只適用於 x64 編譯時。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭 (C)|必要的標頭 (C++)|  
|-------------|---------------------------|-------------------------------|  
|`isnan`, `_isnanf`|\<math.h>|\<math.h> 或 \<cmath>|  
|`_isnan`|\<float.h>|\<float.h> 或 \<cfloat>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [_finite、_finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [_fpclass、_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)