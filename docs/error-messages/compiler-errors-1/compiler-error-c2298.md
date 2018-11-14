---
title: 編譯器錯誤 C2298
ms.date: 11/04/2016
f1_keywords:
- C2298
helpviewer_keywords:
- C2298
ms.assetid: eb0120ad-c850-4bdd-911d-0361229cc859
ms.openlocfilehash: 34957d226f10b4ac27f13be6746eac241101b516
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332045"
---
# <a name="compiler-error-c2298"></a>編譯器錯誤 C2298

'operation': 指標成員函式運算式的作業不合法

成員函式運算式的指標必須呼叫此成員函式。

## <a name="example"></a>範例

下列範例會產生 C2298。

```
// C2298.cpp
#include <stdio.h>

struct X {
   void mf() {
      puts("in X::mf");
   }

   void mf2() {
      puts("in X::mf2");
   }
};

X x;
// pointer to member functions with no params and void return in X
typedef void (X::*pmf_t)();

// a pointer to member function X::mf
void (X::*pmf)() = &X::mf;

int main() {
   int (*pf)();
   pf = x.*pmf;   // C2298
   +(x.*pmf);     // C2298

   pmf_t pf2 = &X::mf2;
   (x.*pf2)();   // uses X::mf2
   (x.*pmf)();   // uses X::mf
}
```

## <a name="example"></a>範例

下列範例會產生 C2298。

```
// C2298_b.cpp
// compile with: /c
void F() {}

class Measure {
public:
   void SetTrackingFunction(void (Measure::*fnc)()) {
      TrackingFunction = this->*fnc;   // C2298
      TrackingFunction = fnc;   // OK
      GlobalTracker = F;   // OK
   }
private:
   void (Measure::*TrackingFunction)(void);
   void (*GlobalTracker)(void);
};
```