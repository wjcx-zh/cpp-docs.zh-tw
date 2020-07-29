---
title: 編譯器錯誤 C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: 5907664ba367d6e4005698e112d0a19f3a2a26e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220375"
---
# <a name="compiler-error-c2274"></a>編譯器錯誤 C2274

' type '： '. ' 運算子的右邊不合法

類型會顯示為成員存取（.）運算子的右運算元。

這個錯誤可能是因為嘗試存取使用者定義的型別轉換所造成。 **`operator`** 在句點和之間使用關鍵字 `type` 。

下列範例會產生 C2286：

```cpp
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```
