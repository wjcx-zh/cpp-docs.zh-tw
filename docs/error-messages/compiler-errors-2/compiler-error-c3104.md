---
title: 編譯器錯誤 C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: 3b2737bd67798fd467649be175d581ca551e1331
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404165"
---
# <a name="compiler-error-c3104"></a>編譯器錯誤 C3104

不合法的屬性引數

您已指定無效的引數的屬性。

請參閱[屬性參數類型](../../extensions/attribute-parameter-types-cpp-component-extensions.md)如需詳細資訊。

此錯誤可能會導致針對視覺效果所進行的編譯器一致性工作C++2005年： 當受管理的陣列傳遞至自訂屬性，陣列的類型不會再推算自彙總初始設定清單。 編譯器現在會要求您指定的陣列，以及初始設定式清單的型別。

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
