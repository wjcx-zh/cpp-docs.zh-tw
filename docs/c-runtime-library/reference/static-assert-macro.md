---
title: _STATIC_ASSERT 巨集
ms.date: 11/04/2016
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: 78544424b727797158109fa3000ee2ebf8066cf7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229320"
---
# <a name="_static_assert-macro"></a>_STATIC_ASSERT 巨集

在編譯時期評估運算式，並在結果為**FALSE**時產生錯誤。

## <a name="syntax"></a>語法

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
評估為非零（**TRUE**）或0（**FALSE**）的運算式（包括指標）。

## <a name="remarks"></a>備註

這個宏與[_ASSERT 和 _ASSERTE 宏](assert-asserte-assert-expr-macros.md)相似，不同之處在于*booleanExpression*是在編譯時期（而不是在執行時間）進行評估。 如果*booleanExpression*評估為**FALSE** （0），則會產生[編譯器錯誤 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) 。

## <a name="example"></a>範例

在此範例中，我們會檢查[sizeof](../../c-language/sizeof-operator-c.md) **`int`** a 是否大於或等於2個位元組，以及[sizeof](../../c-language/sizeof-operator-c.md) a 是否 **`long`** 為1個位元組。 程式將不會編譯，且會產生[編譯器錯誤 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) ，因為大於 **`long`** 1 個位元組。

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

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[_ASSERT、_ASSERTE _ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)<br/>
