---
title: 編譯器錯誤 C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: 8174faed09bdffbdc6974390cceb7c17661eab4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388770"
---
# <a name="compiler-error-c2885"></a>編譯器錯誤 C2885

'class::identifier': 無法有效使用宣告在非類別範圍

您可以使用[使用](../../cpp/using-declaration.md)宣告不正確。

## <a name="example"></a>範例

針對視覺效果所進行的編譯器一致性工作可能會導致此錯誤C++2005年： 已不再能夠有效`using`宣告，以巢狀類型; 您必須明確限定您對巢狀類型，將此類型的每個參考在 命名空間，或建立之 typedef。

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

如果您使用`using`關鍵字與類別成員，C++會要求您定義該成員存在於其他類別 （衍生的類別）。

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