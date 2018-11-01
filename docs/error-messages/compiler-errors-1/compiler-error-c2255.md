---
title: 編譯器錯誤 C2255
ms.date: 11/04/2016
f1_keywords:
- C2255
helpviewer_keywords:
- C2255
ms.assetid: 67dc4cb0-de6b-4405-bd64-d47736367a93
ms.openlocfilehash: ae2c61257af3e1aca2d26ce5f8801999f7bb77c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429389"
---
# <a name="compiler-error-c2255"></a>編譯器錯誤 C2255

'element'：不能在類別定義之外

例如，宣告為 `friend`的非成員函式。

下列範例會產生 C2255：

```
// C2255.cpp
// compile with: /c
class A {
private:
   void func1();
   friend void func2();
};

friend void func1() {}   // C2255
void func2(){}
```