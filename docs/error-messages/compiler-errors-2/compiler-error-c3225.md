---
title: 編譯器錯誤 C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: ed645535300e0a7c4d27f8bed43d3143bae7e97a
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742862"
---
# <a name="compiler-error-c3225"></a>編譯器錯誤 C3225

' arg ' 的泛型型別引數不可為 ' type '，它必須是實數值型別或控制碼類型

泛型型別引數的類型不正確。

如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="examples"></a>範例

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

下列範例會使用 c # 來建立元件。 請注意，條件約束指定泛型型別只能使用實值型別具現化。

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

此範例會使用 c # 撰寫的元件，並違反 MyList 只能使用以外的實值型別來具現化的條件約束 <xref:System.Nullable> 。 下列範例會產生 C3225。

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
