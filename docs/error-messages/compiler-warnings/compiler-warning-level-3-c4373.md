---
title: 編譯器警告 （層級 3） C4373 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4373
dev_langs:
- C++
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fda965fe80fc26731cde7be5a71540e6454a7360
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290175"
---
# <a name="compiler-warning-level-3-c4373"></a>編譯器警告 (層級 3) C4373

> '*函式*': 虛擬函式覆寫*base_function*'，舊版的編譯器不會覆寫當參數差異只不同時 const/volatile 限定詞

## <a name="remarks"></a>備註

您的應用程式在衍生類別中包含的方法會覆寫基底類別中的虛擬方法，且覆寫方法中的參數與虛擬方法的參數僅有 [const](../../cpp/const-cpp.md) 或 [volatile](../../cpp/volatile-cpp.md) 限定詞的差異。 這表示編譯器必須將函式參考繫結至基底或衍生類別中的方法。

在 Visual Studio 2008 之前的編譯器版本將函數繫結至基底類別中的方法，然後發出一則警告訊息。 後續版本的編譯器忽略`const`或`volatile`辨識符號，請將函數繫結至在衍生類別中的方法，然後發出警告**C4373**。 後者的行為符合 C++ 標準。

## <a name="example"></a>範例

下列程式碼範例會產生警告 C4373： 若要解決此問題，您可以建立覆寫基底成員函式中，使用相同的 CV 限定詞，或如果您不想要建立覆寫，您可以提供在衍生類別中的函式不同的名稱。

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

void main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```