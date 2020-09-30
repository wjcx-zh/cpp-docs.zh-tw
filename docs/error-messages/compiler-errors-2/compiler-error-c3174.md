---
title: 編譯器錯誤 C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: a14b59168e0723ea25eefa9ec33a3131837a3aa4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508275"
---
# <a name="compiler-error-c3174"></a>編譯器錯誤 C3174

未指定模組屬性

使用 Visual C++ 屬性的程式也不會使用 [模組](../../windows/attributes/module-cpp.md) 屬性，該屬性在任何使用屬性的程式中都是必要的。

下列範例會產生 C3174：

```cpp
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```
