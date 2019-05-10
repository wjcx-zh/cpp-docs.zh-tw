---
title: 編譯器錯誤 C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 901e9b791616c5684b352c1fda7687f67b895d9c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447368"
---
# <a name="compiler-error-c2027"></a>編譯器錯誤 C2027

使用未定義的類型 'type'

無法使用的類型，直到其定義。 若要解決此錯誤，請務必先參考它完全定義型別。

## <a name="example"></a>範例

下列範例會產生 C2027。

```
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

就可以宣告的宣告，但未定義類型的指標。 但是C++不允許參考未定義的類型。

下列範例會產生 C2027。

```
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