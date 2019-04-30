---
title: 編譯器錯誤 C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: f2fcb75098f18ad113ba68959035b37d9cddd6e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388852"
---
# <a name="compiler-error-c2274"></a>編譯器錯誤 C2274

'type': 當做的右邊不合法 '。 ' 運算子

類型會顯示為成員存取 （.） 運算子的右運算元。

此錯誤可能被因嘗試存取使用者定義型別轉換。 使用關鍵字`operator`之間的週期和`type`。

下列範例會產生 C2286：

```
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