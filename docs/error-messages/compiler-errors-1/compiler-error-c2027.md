---
title: 編譯器錯誤 C2027 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2027
dev_langs:
- C++
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69aae289fbab56cd77e544118909b2d7ef72ae0c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032038"
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

就可以宣告的宣告，但未定義類型的指標。  但 Visual c + + 不允許參考未定義的類型。

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