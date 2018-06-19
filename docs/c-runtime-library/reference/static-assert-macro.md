---
title: _STATIC_ASSERT 巨集 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbbab8314a038d796ebd1a13342f3054e59f3e68
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407362"
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT 巨集

評估在編譯時間運算式，並產生錯誤結果時**FALSE**。

## <a name="syntax"></a>語法

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>參數

*booleanExpression* （包括指標） 的運算式評估為非零 (**TRUE**) 或 0 (**FALSE**)。

## <a name="remarks"></a>備註

這個巨集類似於[_ASSERT 和 _ASSERTE 巨集](assert-asserte-assert-expr-macros.md)，不同之處在於*booleanExpression*在編譯時期評估而不是在執行階段。 如果*booleanExpression*評估為**FALSE** (0)，[編譯器錯誤 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)產生。

## <a name="example"></a>範例

在此範例中，我們會檢查是否[sizeof](../../c-language/sizeof-operator-c.md) **int**大於或等於 2 個位元組和是否[sizeof](../../c-language/sizeof-operator-c.md) **長**是 1 個位元組。 將不會編譯程式，它會產生[編譯器錯誤 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)因為**長**超過 1 個位元組。

```C
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
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集](assert-asserte-assert-expr-macros.md)<br/>
