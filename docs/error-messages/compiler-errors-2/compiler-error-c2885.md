---
title: 編譯器錯誤 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 8174faed09bdffbdc6974390cceb7c17661eab4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652123"
---
# <a name="compiler-error-c2885"></a>編譯器錯誤 C2885

'class::identifier': 無法有效使用宣告在非類別範圍

您可以使用[使用](../../cpp/using-declaration.md)宣告不正確。

## <a name="example"></a>範例

針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致此錯誤： 已不再有效有`using`宣告，以巢狀類型; 您必須明確限定您對巢狀類型，將類型放在名稱中的每個參考空間，或建立 typedef。

下列範例會產生 C2885。

```
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

如果您使用`using`關鍵字與類別成員，c + + 需要您定義該成員存在於其他類別 （衍生的類別）。

下列範例會產生 C2885。

```
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