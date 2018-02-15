---
title: fpclassify | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81a2c9c5237d455908e1d0e4f58bff87418a7f8b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="fpclassify"></a>fpclassify
傳回引數的浮點分類。  
  
## <a name="syntax"></a>語法  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 要測試的浮點值。  
  
## <a name="return-value"></a>傳回值  
 `fpclassify` 會傳回整數值，指出 `x` 引數的浮點類別。 此表格顯示 `fpclassify` (定義於 \<math.h>) 所傳回的可能值。  
  
|值|描述|  
|-----------|-----------------|  
|`FP_NAN`|無訊息、訊號或不確定的 NaN|  
|`FP_INFINITE`|正或負無限大|  
|`FP_NORMAL`|正或負標準化非零值|  
|`FP_SUBNORMAL`|正或負異常化值|  
|`FP_ZERO`|正或負零值|  
  
## <a name="remarks"></a>備註  
 在 C 中，`fpclassify` 是巨集；在 C++ 中，`fpclassify` 是使用 `float`、`double` 或 `long double` 之引數類型所多載的函式。 在任一情況下，傳回值取決於引數運算式的有效類型，而非任何中繼呈現。 例如，轉換成 `float` 時，一般 `double` 或 `long double` 值可以是無限大、異常或零值。  
  
## <a name="requirements"></a>需求  
  
|函式/巨集|必要的標頭 (C)|必要的標頭 (C++)|  
|---------------------|---------------------------|-------------------------------|  
|`fpclassify`|\<math.h>|\<math.h> 或 \<cmath>|  
  
 `fpclassify` 巨集和 `fpclassify` 函式符合 C99 和 C++11 規格。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [isnan、_isnan、_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)