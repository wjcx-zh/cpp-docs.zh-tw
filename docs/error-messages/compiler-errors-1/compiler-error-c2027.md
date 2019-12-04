---
title: 編譯器錯誤 C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 62cf208d9d0025afba06d32a15b9a1e50777c473
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750997"
---
# <a name="compiler-error-c2027"></a>編譯器錯誤 C2027

使用未定義的類型 ' type '

類型必須在定義之後才能使用。 若要解決此錯誤，請確定已完整定義類型，然後再加以參考。

## <a name="example"></a>範例

下列範例會產生 C2027。

```cpp
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

## <a name="example"></a>範例

您可以宣告指向已宣告但未定義之類型的指標。 但C++不允許參考未定義的類型。

下列範例會產生 C2027。

```cpp
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```
