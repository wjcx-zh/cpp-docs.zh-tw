---
title: 編譯器警告 (層級 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 5891d4679b74695f187fb50bb24fe941882fdcc7
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518344"
---
# <a name="compiler-warning-level-3-c4373"></a>編譯器警告 (層級 3) C4373

> '*function*'：虛擬函式覆寫 '*base_function*'，當參數只有 const/volatile 限定詞不同時，舊版編譯器不會覆寫

## <a name="remarks"></a>備註

您的應用程式在衍生類別中包含的方法會覆寫基底類別中的虛擬方法，且覆寫方法中的參數與虛擬方法的參數僅有 [const](../../cpp/const-cpp.md) 或 [volatile](../../cpp/volatile-cpp.md) 限定詞的差異。 這表示編譯器必須將函式參考繫結至基底或衍生類別中的方法。

Visual Studio 2008 之前的編譯器版本會將函式系結至基類中的方法，然後發出警告訊息。 後續版本的編譯器會忽略 `const` 或 `volatile` 辨識符號，將函式系結至衍生類別中的方法，然後發出警告**C4373**。 後者的行為符合 C++ 標準。

## <a name="example"></a>範例

下列程式碼範例會產生警告 C4373： 若要解決這個問題，您可以讓覆寫使用與基底成員函式相同的 CV 限定詞，或如果您不想要建立覆寫，您可以為衍生類別中的函數提供不同的名稱。

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
