---
title: 編譯器錯誤 C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: d7cf39e89f70f27471fb3a251aac12793f1fb33b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760292"
---
# <a name="compiler-error-c2681"></a>編譯器錯誤 C2681

' type '：名稱的運算式類型無效

轉換運算子嘗試從不正確類型進行轉換。 例如，如果您使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子將運算式轉換成指標類型，則來源運算式必須是指標。

下列範例會產生 C2681：

```cpp
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```
