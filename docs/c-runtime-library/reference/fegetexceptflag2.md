---
title: fegetexceptflag2 | Microsoft Docs
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
- fegetexceptflag
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetexceptflag
- fenv/fegetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b1180db74e0000f24e12b6d411460e6a4efc9de
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="fegetexceptflag"></a>fegetexceptflag
儲存目前的指定浮點例外狀況旗標的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
int fegetexceptflag(   
   fexcept_t* pstatus,   
   int excepts   
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `pstatus`  
 `fexcept_t` 物件的指標，包含 `excepts` 指定的例外狀況旗標目前的值。  
  
 `excepts`  
 要儲存在 `pstatus` 中的浮點例外狀況旗標。  
  
## <a name="return-value"></a>傳回值  
 成功時會傳回 0。 否則，傳回非零值。  
  
## <a name="remarks"></a>備註  
 `fegetexceptflag` 函式會將 `excepts` 指定的浮點例外狀況狀態旗標的目前狀態儲存在 `pstatus` 指向的 `fexcept_t` 物件中。  `pstatus` 必須指向有效的 `fexcept_t` 物件，否則不定義後續行為。 `fegetexceptflag` 函式支援這些在 \<fenv.h> 中定義的例外狀況巨集︰  
  
|例外狀況巨集|描述|  
|---------------------|-----------------|  
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|  
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|  
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|  
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|  
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|  
|FE_ALLEXCEPT|所有受支援浮點例外狀況的位元 OR。|  
  
 `excepts` 引數可以是零、受支援的浮點例外狀況巨集之一，或兩個或以上巨集的位元 OR。 未定義任何其他引數值的效果。  
  
 若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`fegetexceptflag`|\<fenv.h>|\<cfenv>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)