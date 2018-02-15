---
title: feraiseexcept | Microsoft Docs
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
- feraiseexcept
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
- feraiseexcept
- fenv/feraiseexcept
dev_langs:
- C++
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaaa1848af2c8a7831017f6332afa988c305fe05
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="feraiseexcept"></a>feraiseexcept
引發指定的浮點例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
int feraiseexcept(  
   int excepts  
);  
```  
  
#### <a name="parameters"></a>參數  
 `excepts`  
 要引發的浮點例外狀況。  
  
## <a name="return-value"></a>傳回值  
 如果成功引發所有指定的例外狀況，則傳回 0。  
  
## <a name="remarks"></a>備註  
 `feraiseexcept` 函式嘗試引發 `excepts` 指定的浮點例外狀況。   `feraiseexcept` 函式支援這些在 \<fenv.h> 中定義的例外狀況巨集︰  
  
|例外狀況巨集|描述|  
|---------------------|-----------------|  
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|  
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|  
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|  
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|  
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|  
|FE_ALLEXCEPT|所有受支援浮點例外狀況的位元 OR。|  
  
 `excepts` 引數可以是零、例外狀況巨集之一，或兩個或以上受支援例外狀況巨集的位元 OR。 如果其中一個指定的例外狀況巨集是 FE_OVERFLOW 或 FE_UNDERFLOW，則可能會發生副作用 FE_INEXACT 例外狀況。  
  
 若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。  
  
 **Microsoft 特有︰**`excepts` 中指定的例外狀況會依照 FE_INVALID、FE_DIVBYZERO、FE_OVERFLOW、FE_UNDERFLOW、FE_INEXACT 順序引發。 不過，FE_INEXACT 可以在 FE_OVERFLOW 或 FE_UNDERFLOW 引發時引發，即使 `excepts` 中未指定。 **結束 Microsoft 特有**  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`feraiseexcept`|\<fenv.h>|\<cfenv>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)