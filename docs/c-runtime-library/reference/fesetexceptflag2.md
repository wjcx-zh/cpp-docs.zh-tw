---
title: fesetexceptflag2 | Microsoft Docs
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
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: 7
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 2283d258a15fb131367d5d24a921c0a84a31e91d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="fesetexceptflag"></a>fesetexceptflag
在目前的浮點環境中設定指定的浮點狀態旗標。  
  
## <a name="syntax"></a>語法  
  
```  
int fesetexceptflag(  
     const fexcept_t *pstatus,  
     int excepts  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstatus`  
 `fexcept_t` 物件的指標，包含要設定的例外狀況狀態旗標值。 物件可能是由先前呼叫 [fegetexceptflag](fegetexceptflag2.md) 所設定。  
  
 `excepts`  
 要設定的浮點例外狀況狀態旗標。  
  
## <a name="return-value"></a>傳回值  
 如果成功設定所有指定的例外狀況狀態旗標，則傳回 0。 否則，傳回非零值。  
  
## <a name="remarks"></a>備註  
 `fesetexceptflag` 函式會將 `excepts` 指定的浮點例外狀況狀態旗標的狀態，設成 `pstatus` 指向的 `fexcept_t` 物件的對應值。  它不會引發例外狀況。 `pstatus` 指標必須指向有效的 `fexcept_t` 物件，否則不定義後續行為。 `fesetexceptflag` 函式支援這些在 \<fenv.h> 中定義的 `excepts` 例外狀況巨集值︰  
  
|例外狀況巨集|說明|  
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
  
|函式|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`fesetexceptflag`|\<fenv.h>|\<cfenv>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetexceptflag](../../c-runtime-library/reference/fegetexceptflag2.md)
