---
title: 編譯器錯誤 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 1953cb8fb9f80c5c1f967e10583c2b7303075f59
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742667"
---
# <a name="compiler-error-c2885"></a>編譯器錯誤 C2885

' class：： identifier '：在非類別範圍中不是有效的 using 宣告

您使用了不正確的 [using](../../cpp/using-declaration.md) 宣告。

這項錯誤可能是因為針對 Visual Studio 2005 完成的編譯器一致性工作所產生：它不再是具有巢狀型別宣告的有效方式 **`using`** ; 您必須明確限定您對巢狀型別所做的每個參考、將類型放在命名空間中，或建立 typedef。

## <a name="examples"></a>範例

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

如果您使用 **`using`** 關鍵字搭配類別成員，則 c + + 會要求您在 (衍生類別) 的另一個類別中定義該成員。

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
