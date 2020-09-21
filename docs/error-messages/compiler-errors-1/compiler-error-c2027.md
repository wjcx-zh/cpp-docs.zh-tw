---
title: 編譯器錯誤 C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 59d0e5d5a5f0957f2d73cdb863ccee9a2dd2a026
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743252"
---
# <a name="compiler-error-c2027"></a>編譯器錯誤 C2027

使用未定義的類型 ' type '

在定義型別之前，無法使用型別。 若要解決此錯誤，請確定類型已在參考之前完整定義。

## <a name="examples"></a>範例

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

您可以宣告指向已宣告但未定義之類型的指標。 但 c + + 不允許參考未定義的類型。

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
