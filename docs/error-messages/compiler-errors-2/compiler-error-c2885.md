---
title: 編譯器錯誤 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 9b6b7bb54d5dce48dc6fce517eb0c909b0284da2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233440"
---
# <a name="compiler-error-c2885"></a>編譯器錯誤 C2885

' class：： identifier '：在非類別範圍中不是有效的 using 宣告

您使用了不正確的[using](../../cpp/using-declaration.md)宣告。

## <a name="example"></a>範例

這項錯誤可能會因為針對 Visual Studio 2005 所做的編譯器一致性工作而產生：已不再有效，對嵌套型別進行宣告 **`using`** 。您必須明確限定您對嵌套型別所做的每個參考，將型別放在命名空間中，或建立 typedef。

下列範例會產生 C2885。

```cpp
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

## <a name="example"></a>範例

如果您使用 **`using`** 關鍵字搭配類別成員，c + + 會要求您在另一個類別（衍生類別）內定義該成員。

下列範例會產生 C2885。

```cpp
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```
