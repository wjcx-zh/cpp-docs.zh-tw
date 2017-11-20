---
title: fetestexcept1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fetestexcept
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
- fetestexcept
- fenv/fetestexcept
dev_langs: C++
helpviewer_keywords: fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2fa4448bc71fc8b01abffaa0655f63e6ef474a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="fetestexcept"></a>fetestexcept
決定目前設定哪一個指定的浮點例外狀況狀態旗標。  
  
## <a name="syntax"></a>語法  
  
```  
int fetestexcept(  
   int excepts  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `excepts`  
 要測試的浮點狀態旗標位元 OR。  
  
## <a name="return-value"></a>傳回值  
 成功時會傳回包含浮點例外狀況巨集位元 OR 的遮罩設定，這些巨集對應目前設定的例外狀況狀態旗標。 如未設定任何例外狀況，則傳回 0。  
  
## <a name="remarks"></a>備註  
 使用 fetestexcept 函式判斷浮點運算引發的例外狀況。 使用 `excepts` 參數指定要測試的例外狀況狀態旗標。 `fetestexcept` 函式會使用在 `excepts` 中以 \<fenv.h > 定義的這些例外狀況巨集並傳回值︰  
  
|例外狀況巨集|說明|  
|---------------------|-----------------|  
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|  
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|  
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|  
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|  
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|  
|FE_ALLEXCEPT|所有受支援浮點例外狀況的位元 OR。|  
  
 指定的 `excepts` 引數可以是 0、受支援的浮點例外狀況巨集之一，或兩個或以上巨集的位元 OR。 未定義任何其他 `excepts` 引數值的效果。  
  
 若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>需求  
  
|函式|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`fetestexcept`|\<fenv.h>|\<cfenv>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feraiseexcept](../../c-runtime-library/reference/feraiseexcept.md)