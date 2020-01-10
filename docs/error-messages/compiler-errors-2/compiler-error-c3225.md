---
title: 編譯器錯誤 C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: 1caa1e7ce787ffc14e615c946b5d670c75e0332a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757614"
---
# <a name="compiler-error-c3225"></a>編譯器錯誤 C3225

' arg ' 的泛型型別引數不可以是 ' type '，它必須是實數值型別或控制碼類型

泛型型別引數不是正確的型別。

如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

您無法具現化具有原生類型的泛型型別。 下列範例會產生 C3225。

```cpp
// C3225.cpp
// compile with: /clr
class A {};

ref class B {};

generic <class T>
ref class C {};

int main() {
   C<A>^ c = gcnew C<A>;   // C3225
   C<B^>^ c2 = gcnew C<B^>;   // OK
}
```

## <a name="example"></a>範例

下列範例會使用來C#建立元件。 請注意，條件約束指定泛型型別只能以實值型別具現化。

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>範例

這個範例會使用C#撰寫的元件，而且會違反條件約束，MyList 只能以 <xref:System.Nullable>以外的實值型別具現化。 下列範例會產生 C3225。

```cpp
// C3225_c.cpp
// compile with: /clr
#using "C3225_b.dll"
ref class A {};
value class B {};
int main() {
   MyList<A> x;   // C3225
   MyList<B> y;   // OK
}
```
