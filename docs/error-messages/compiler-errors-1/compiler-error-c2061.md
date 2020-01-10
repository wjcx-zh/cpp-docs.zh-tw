---
title: 編譯器錯誤 C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: dc64852523b6b56bc506260576e3c79164628340
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735927"
---
# <a name="compiler-error-c2061"></a>編譯器錯誤 C2061

語法錯誤：識別碼 ' identifier '

編譯器找到的識別碼不在預期的位置。 在使用之前，請確定已宣告 `identifier`。

初始化運算式可以用括弧括住。 若要避免這個問題，請將宣告子括在括弧中，或將它設為 `typedef`。

當編譯器偵測到運算式做為類別樣板引數時，也可能會造成此錯誤;使用[typename](../../cpp/typename.md)來告訴編譯器它是一種類型。

下列範例會產生 C2061：

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

如果您將實例名稱傳遞至[typeid](../../extensions/typeid-cpp-component-extensions.md)，可能會發生 C2061：

```cpp
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```
