---
title: 編譯器錯誤 C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: fee023809246634f2f3da266a718e45861eae76e
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447842"
---
# <a name="compiler-error-c3104"></a>編譯器錯誤 C3104

不合法的屬性引數

您已指定無效的引數的屬性。

請參閱[屬性參數類型](../../extensions/attribute-parameter-types-cpp-component-extensions.md)如需詳細資訊。

針對 Visual Studio 2005 所進行的編譯器一致性工作可能會導致此錯誤： 當受管理的陣列傳遞至自訂屬性，陣列的類型不會再推算自彙總初始設定清單。 編譯器現在會要求您指定的陣列，以及初始設定式清單的型別。

## <a name="example"></a>範例

下列範例會產生 C3104。

```
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="example"></a>範例

下列範例會產生 C3104。

```
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
