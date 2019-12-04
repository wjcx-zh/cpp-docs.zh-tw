---
title: 編譯器錯誤 C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: 9cd46f7a8a0762fcae2bdec15b9b4be6384adb25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758680"
---
# <a name="compiler-error-c2273"></a>編譯器錯誤 C2273

' type '：不合法的 as '-> ' 運算子的右側

類型會顯示為 `->` 運算子的右運算元。

這個錯誤可能是因為嘗試存取使用者定義的型別轉換所造成。 在-> 和 `type`之間使用關鍵字 `operator`。

下列範例會產生 C2273：

```cpp
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```
