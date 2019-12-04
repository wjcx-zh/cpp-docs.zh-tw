---
title: 編譯器錯誤 C3351
ms.date: 11/04/2016
f1_keywords:
- C3351
helpviewer_keywords:
- C3351
ms.assetid: c021bbbe-1067-4f51-af4f-940d2b792eb5
ms.openlocfilehash: d93d6b08268aa8d6a7a7ad2e2086f4799417bbb4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737461"
---
# <a name="compiler-error-c3351"></a>編譯器錯誤 C3351

'object': 委派建構函式：第二個引數必須是靜態成員函式或全域函式的位址

編譯器必須有宣告為 `static`之函式的位址。

下列範例會產生 C3351：

```cpp
// C3351a.cpp
// compile with: /clr
delegate int D(int, int);

ref class C {
public:
   int mf(int, int) {
      return 1;
   }

   static int mf2(int, int) {
      return 1;
   }
};

int main() {
   System::Delegate ^pD = gcnew D(nullptr, &C::mf);   // C3351
   System::Delegate ^pD2 = gcnew D(&C::mf2);
}
```
