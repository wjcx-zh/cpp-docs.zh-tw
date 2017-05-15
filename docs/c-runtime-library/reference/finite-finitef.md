---
title: "_finite、_finitef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _finite
- _finitef
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
- finite
- _finite
- _finitef
- math/_finite
- math/_finitef
- float/_finite
dev_langs:
- C++
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: 15
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
ms.openlocfilehash: 90eff10a00ecfdfd772acc7caa624ff35dd392d7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="finite-finitef"></a>_finite、_finitef
判斷指定的浮點數值是否有限。  
  
## <a name="syntax"></a>語法  
  
```  
int _finite(   
   double x   
);  
  
int _finitef(   
   float x   
); /* x64 and ARM/ARM64 only */  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 要測試的浮點值。  
  
## <a name="return-value"></a>傳回值  
 同時`_finite`和`_finitef`傳回非零值，如果引數*x*為有限; 也就是說，如果-INF < `x` < + INF。 如果引數為無限或 NAN，它會傳回 0。  
  
## <a name="remarks"></a>備註  
 `_finite` 和 `_finitef` 函式為 Microsoft 特有。 只有在針對 x86、ARM 或 ARM64 平台進行編譯時，才能使用 `_finitef` 函式。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭 (C)|必要的標頭 (C++)|  
|--------------|---------------------------|-------------------------------|  
|`_finite`|\<float.h> 或 \<math.h>|\<float.h>、\<math.h>、\<cfloat> 或 \<cmath>|  
|`_finitef`|\<math.h>|\<math.h> 或 \<cmath>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [isnan、_isnan、_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [_fpclass、_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)
