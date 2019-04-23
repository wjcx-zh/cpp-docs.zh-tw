---
title: 編譯器錯誤 C3352
ms.date: 11/04/2016
f1_keywords:
- C3352
helpviewer_keywords:
- C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
ms.openlocfilehash: 6641f05c8daa5ad505c0bcb8d29a369ad5fd9a9a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778328"
---
# <a name="compiler-error-c3352"></a>編譯器錯誤 C3352

'function': 指定的函式委派類型 'type' 不相符

參數會列出`function`和委派不相符。

如需詳細資訊，請參閱 <<c0> [ 委派 (C++元件擴充功能)](../../extensions/delegate-cpp-component-extensions.md)。</c0>

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
