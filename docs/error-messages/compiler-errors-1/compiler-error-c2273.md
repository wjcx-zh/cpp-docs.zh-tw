---
title: 編譯器錯誤 C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: f5780c299eb4da03ece3611ee55062ee7ebcdaae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212783"
---
# <a name="compiler-error-c2273"></a>編譯器錯誤 C2273

' type '：不合法的 as '-> ' 運算子的右側

型別會顯示為運算子的右運算元 `->` 。

這個錯誤可能是因為嘗試存取使用者定義的型別轉換所造成。 在 **`operator`** -> 和之間使用關鍵字 `type` 。

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
