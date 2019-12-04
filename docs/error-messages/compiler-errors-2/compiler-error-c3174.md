---
title: 編譯器錯誤 C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: 868d43e0796b7a6ab7398573e8b61efcb627d8a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761721"
---
# <a name="compiler-error-c3174"></a>編譯器錯誤 C3174

未指定 module 屬性

使用視覺化C++屬性的程式也不會使用[模組](../../windows/module-cpp.md)屬性，這在使用屬性的任何程式中都是必要的。

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
