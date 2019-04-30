---
title: 編譯器錯誤 C2385
ms.date: 11/04/2016
f1_keywords:
- C2385
helpviewer_keywords:
- C2385
ms.assetid: 6d3dd1f2-e56d-49d7-865c-6a9acdb17417
ms.openlocfilehash: bffb4c1088c41832e69b0c6f161b47f6f9f08d06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393697"
---
# <a name="compiler-error-c2385"></a>編譯器錯誤 C2385

'member' 的模稜兩可的存取權

成員可以衍生自多個物件 （它繼承自多個物件）。  若要解決這個錯誤，

- 提供型別轉換，讓成員模稜兩可。

- 重新命名在基底類別模稜兩可的成員。

## <a name="example"></a>範例

下列範例會產生 C2385。

```
// C2385.cpp
// C2385 expected
#include <stdio.h>

struct A
{
    void x(int i)
    {
        printf_s("\nIn A::x");
    }
};

struct B
{
    void x(char c)
    {
        printf_s("\nIn B::x");
    }
};

// Delete the following line to resolve.
struct C : A, B {}

// Uncomment the following 4 lines to resolve.
// struct C : A, B
// {
//     using B::x;
//     using A::x;
// };

int main()
{
    C aC;
    aC.x(100);
    aC.x('c');
}

struct C : A, B
{
    using B::x;
    using A::x;
};
```