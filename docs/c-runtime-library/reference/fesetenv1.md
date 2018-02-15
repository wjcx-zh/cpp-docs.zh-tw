---
title: "fesetenv |Microsoft 文件"
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
- fesetenv
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
- fesetenv
- fenv/fesetenv
dev_langs:
- C++
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2717c0fee2582cac3c9013f3f49ff37744cbde9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="fesetenv"></a>fesetenv
設定目前的浮點環境。  
  
## <a name="syntax"></a>語法  
  
```  
int fesetenv(  
   const fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>參數  
 `penv`  
 `fenv_t` 物件的指標，包含 [fegetenv](fegetenv1.md) 或 [feholdexcept](feholdexcept2.md) 呼叫設定的浮點環境。 您也可以使用 FE_DFL_ENV 巨集指定預設啟動浮點環境。  
  
## <a name="return-value"></a>傳回值  
 如果成功設定環境，則傳回 0。 否則，傳回非零值。  
  
## <a name="remarks"></a>備註  
 `fesetenv` 函式會從由儲存在 `penv` 指向之 `fenv_t` 物件的值中，設定目前的浮點環境。 浮點點環境是一組會影響浮點計算的狀態旗標和控制項模式。 這包括捨入模式以及處理浮點例外狀況的狀態旗標。  如果 `penv` 不是 FE_DFL_ENV 或不指向有效的 `fenv_t` 物件，則不定義後續行為。  
  
 呼叫此函式會設定 `penv` 物件中的例外狀況狀態旗標，但它不會引發這些例外狀況。  
  
 若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`fesetenv`|\<fenv.h>|\<cfenv>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)