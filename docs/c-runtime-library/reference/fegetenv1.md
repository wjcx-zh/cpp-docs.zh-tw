---
title: fegetenv1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fetegenv
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
- fegetenv
- fenv/fegetenv
dev_langs: C++
helpviewer_keywords: fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3da1a5837a2c2e3a2cd1c7987363b251bc67b567
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fegetenv"></a>fegetenv
將目前的浮點環境儲存在指定的物件中。  
  
## <a name="syntax"></a>語法  
  
```  
int fegetenv(  
   fenv_t *penv  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `penv`  
 `fenv_t` 物件的指標，包含目前的浮點環境值。  
  
## <a name="return-value"></a>傳回值  
 如果浮點環境已成功儲存在 `penv` 中，則傳回 0。 否則，傳回非零值。  
  
## <a name="remarks"></a>備註  
 `fegetenv` 函式會將目前的浮點環境儲存在 `penv` 指向的物件中。 浮點點環境是一組會影響浮點計算的狀態旗標和控制項模式。 這包括捨入方向模式以及處理浮點例外狀況的狀態旗標。  如果 `penv` 不指向有效的 `fenv_t` 物件，則不定義後續行為。  
  
 若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`fegetenv`|\<fenv.h>|\<cfenv>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetenv](../../c-runtime-library/reference/fesetenv1.md)