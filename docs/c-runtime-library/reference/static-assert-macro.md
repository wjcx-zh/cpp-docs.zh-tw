---
title: "_STATIC_ASSERT 巨集 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords:
- _STATIC_ASSERT
dev_langs:
- C++
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: 6
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 265796cdebbed1c0a067c44bbe6b71077be44a2b
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="staticassert-macro"></a>_STATIC_ASSERT 巨集
在編譯期間評估運算式，並在結果為 `FALSE` 時產生錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### <a name="parameters"></a>參數  
 `booleanExpression`  
 評估為非零 (`TRUE`) 或 0 (`FALSE`) 的運算式 (包括指標)。  
  
## <a name="remarks"></a>備註  
 這個巨集與 [_ASSERT 和 _ASSERTE 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)類似，差異在於是在編譯期間評估 `booleanExpression`，而不是執行階段。 如果 `booleanExpression` 評估為 `FALSE` (0)，則會產生[編譯器錯誤 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)。  
  
## <a name="example"></a>範例  
 在此範例中，檢查 `int` 的 `sizeof` 是否大於或等於 2 個位元組，以及 `long` 的 `sizeof` 是否為 1 個位元組。 因為 `long` 大於 1 個位元組，所以將不會編譯程式，並且會產生[編譯器錯誤 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)。  
  
```  
// crt__static_assert.c  
  
#include <crtdbg.h>  
#include <stdio.h>  
  
_STATIC_ASSERT(sizeof(int) >= 2);  
_STATIC_ASSERT(sizeof(long) == 1);  // C2466  
  
int main()  
{  
    printf("I am sure that sizeof(int) will be >= 2: %d\n",  
        sizeof(int));  
    printf("I am not so sure that sizeof(long) == 1: %d\n",  
        sizeof(long));  
}  
```  
  
## <a name="requirements"></a>需求  
  
|巨集|必要的標頭|  
|-----------|---------------------|  
|`_STATIC_ASSERT`|\<crtdbg.h>|  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)
