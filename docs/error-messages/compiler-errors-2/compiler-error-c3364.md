---
title: 編譯器錯誤 C3364
ms.date: 11/04/2016
f1_keywords:
- C3364
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
ms.openlocfilehash: e99ab3919edcfb883701c08c52cd7aad60cd4591
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400353"
---
# <a name="compiler-error-c3364"></a>編譯器錯誤 C3364

'delegate': 委派建構函式： 引數必須是受管理的類別成員函式或全域函式指標

委派的建構函式的第二個參數會使用成員函式的位址或任何類別的靜態成員函式的位址。 兩者會被視為簡單的位址。

下列範例會產生 C3364:

```
// C3364_2.cpp
// compile with: /clr

delegate int D( int, int );

ref class C {
public:
   int mf( int, int ) {
      return 1;
   }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364

   // try the following line instead
   // System::Delegate^ pD = gcnew D(pC, &C::mf);
}
```
