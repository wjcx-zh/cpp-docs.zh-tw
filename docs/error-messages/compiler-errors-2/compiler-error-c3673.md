---
title: 編譯器錯誤 C3673
ms.date: 11/04/2016
f1_keywords:
- C3673
helpviewer_keywords:
- C3673
ms.assetid: bb6d2079-05af-4e2c-be0e-75c892e6c590
ms.openlocfilehash: 80e9a80d822a9da0e9ae388991f3dbc78bfca0db
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686713"
---
# <a name="compiler-error-c3673"></a>編譯器錯誤 C3673

' type '：類別沒有複製函式

需要使用者定義的函式，才能複製 CLR ref 類型的物件。 如需詳細資訊，請參閱參考型別的 [c + + 堆疊語義](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="examples"></a>範例

下列範例會產生 C3673。

```cpp
// C3673.cpp
// compile with: /clr
public ref struct R {
public:
   R() {}
   // Uncomment the following line to resolve.
   // R(R% p) {}
};

int main() {
   R r;
   R s = r;   // C3673
}
```

下列範例會產生 C3673。

```cpp
// C3673_b.cpp
// compile with: /clr /c
// C3673 expected
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   // Uncomment the following line to resolve.
   // MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // OK, no arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // OK, named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```
