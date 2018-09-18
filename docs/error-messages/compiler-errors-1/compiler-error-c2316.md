---
title: 編譯器錯誤 C2316 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2868d3a81fcbc94d8b20adcdc775363eb0a8eaeb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033013"
---
# <a name="compiler-error-c2316"></a>編譯器錯誤 C2316

> '*例外狀況*': 無法攔截，因為無法存取解構函式及/或複製建構函式

以傳值方式或以傳址方式攔截到例外狀況，但是複製建構函式及/或指派運算子都無法存取。

此程式碼版本的 Visual Studio 2003 之前的 Visual c + + 已接受，但現在會產生錯誤。

在 Visual Studio 2015 的合規性變更進行套用至不正確的 catch 陳述式的 MFC 例外狀況衍生自這個錯誤`CException`。 因為`CException`繼承私用複製建構函式，類別和其衍生項目不可複製的而且不能傳值方式傳遞，這也表示他們無法依值攔截。 Catch 依先前會導致在執行階段，無法攔截的例外狀況的值攔截 MFC 例外狀況的陳述式，但現在編譯器正確地識別出這種情況以及報告錯誤 C2316。 若要修正此問題，我們建議您使用 MFC TRY/CATCH 巨集，而不是撰寫自己的例外狀況處理常式，但不適合您的程式碼，如果攔截 MFC 例外狀況的參考而。

## <a name="example"></a>範例

下列範例會產生 C2316：

```
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

extern "C" int printf_s(const char*, ...);

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&)
    {
    }
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b) {   // C2316
        printf_s("Caught an exception!\n");
    }
}
```