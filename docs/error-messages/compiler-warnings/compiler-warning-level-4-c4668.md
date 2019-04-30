---
title: 編譯器警告 (層級 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 11d96941a1efddde87068af8829e24259f2fa312
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408156"
---
# <a name="compiler-warning-level-4-c4668"></a>編譯器警告 (層級 4) C4668

'symbol' 未定義成前置處理器巨集，以 '0' 取代 'directives'

前置處理器指示詞搭配使用未定義的符號。 符號會評估為 false。 若要定義符號，您可以使用[#define 指示詞](../../preprocessor/hash-define-directive-c-cpp.md)或是[/D](../../build/reference/d-preprocessor-definitions.md)編譯器選項。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

## <a name="example"></a>範例

下列範例會產生 C4668:

```
// C4668.cpp
// compile with: /W4
#include <stdio.h>

#pragma warning (default : 4668)   // turn warning on

int main()
{
    #if q   // C4668, q is not defined
        printf_s("defined");
    #else
        printf_s("undefined");
    #endif
}
```