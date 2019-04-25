---
title: 編譯器錯誤 C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: cae0572002c849fb5aed771993d3a89ed82c726a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174012"
---
# <a name="compiler-error-c3225"></a>編譯器錯誤 C3225

'arg' 的泛型類型引數不可為 'type'，它必須是實值類型或控制代碼類型

泛型類型引數不是正確的型別。

如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

您無法具現化原生類型的泛型型別。 下列範例會產生 C3225。

```
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

下列範例會建立使用 C# 的元件。 請注意，條件約束指定泛型型別只產生使用實值型別。

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>範例

此範例會使用來自 C#-撰寫元件，且違反條件約束，只能是 MyList 以外使用實值型別執行個體化<xref:System.Nullable>。 下列範例會產生 C3225。

```
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