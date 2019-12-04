---
title: 編譯器錯誤 C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: b111448e7e9d8260a5101d05996a670013936894
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746405"
---
# <a name="compiler-error-c2533"></a>編譯器錯誤 C2533

'identifier'：建構函式不允許傳回型別

建構函式不能有傳回類型 (甚至是 `void` 傳回類型也不可以)。

此錯誤的常見來源是類別定義結尾與第一個建構函式實作之間遺漏分號。 編譯器會將類別視為建構函式的傳回型別定義，並產生 C2533。

下列範例會產生 C2533，並示範如何修正此問題：

```cpp
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```
