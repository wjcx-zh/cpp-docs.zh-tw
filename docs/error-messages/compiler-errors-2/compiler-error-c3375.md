---
title: 編譯器錯誤 C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: cf92f0fabecfa7292a4d6a8644746c489cbf139f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759746"
---
# <a name="compiler-error-c3375"></a>編譯器錯誤 C3375

'function' : 模稜兩可的委派函式

委派具現化可能已指派給靜態成員函式，或作為執行個體函式的未繫結委派，因此編譯器會發出這個錯誤。

如需詳細資訊，請參閱[委派（C++元件擴充功能）](../../extensions/delegate-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3375。

```cpp
// C3375.cpp
// compile with: /clr
ref struct R {
   static void f(R^) {}
   void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::f);   // C3375
}
```
