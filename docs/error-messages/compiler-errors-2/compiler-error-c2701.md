---
title: 編譯器錯誤 C2701
ms.date: 11/04/2016
f1_keywords:
- C2701
helpviewer_keywords:
- C2701
ms.assetid: 31cf2ab7-ced9-4f75-aa51-e169e20407fb
ms.openlocfilehash: b16ddb16d98a81e53b29ff51e41d19073200a2e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161286"
---
# <a name="compiler-error-c2701"></a>編譯器錯誤 C2701

'function': 不可本機類別的 friend 函式樣板。

區域類別不能有的樣板函式做為 friend 函式。

下列範例會產生 C2701:

```
// C2701.cpp
// compile with: /c
template<typename T>   // OK
void f1(const T &);

void MyFunction() {
   class MyClass {
      template<typename T> friend void f2(const T &);   // C2701
   };
}
```