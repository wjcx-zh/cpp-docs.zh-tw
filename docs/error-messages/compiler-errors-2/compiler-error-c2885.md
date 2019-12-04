---
title: 編譯器錯誤 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: e60f3fff2ef61f4d6374072c05a2ad3e64a57031
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760924"
---
# <a name="compiler-error-c2885"></a>編譯器錯誤 C2885

' class：： identifier '：在非類別範圍中不是有效的 using 宣告

您使用了不正確的[using](../../cpp/using-declaration.md)宣告。

## <a name="example"></a>範例

這項錯誤可能會因為針對 Visual Studio 2005 而完成的編譯器一致性工作而產生： `using` 宣告為嵌套的類型已經失效。您必須明確限定您對巢狀型別所做的每個參考、將類型放在命名空間中，或建立 typedef。

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

如果您使用 `using` 關鍵字搭配類別成員， C++則需要在另一個類別（衍生類別）中定義該成員。

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
