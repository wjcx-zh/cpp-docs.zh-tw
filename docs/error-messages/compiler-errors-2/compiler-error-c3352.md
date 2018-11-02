---
title: 編譯器錯誤 C3352
ms.date: 11/04/2016
f1_keywords:
- C3352
helpviewer_keywords:
- C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
ms.openlocfilehash: c45ce5e2e72c6a987a0053cb4b1bbb151c149faf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496530"
---
# <a name="compiler-error-c3352"></a>編譯器錯誤 C3352

'function': 指定的函式委派類型 'type' 不相符

參數會列出`function`和委派不相符。

如需詳細資訊，請參閱 <<c0> [ 委派 （c + + 元件延伸模組）](../../windows/delegate-cpp-component-extensions.md)。

下列範例會產生 C3352:

```
// C3352.cpp
// compile with: /clr
delegate int D( int, int );
ref class C {
public:
   int mf( int ) {
      return 1;
   }

   // Uncomment the following line to resolve.
   // int mf(int, int) { return 1; }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352
}
```
