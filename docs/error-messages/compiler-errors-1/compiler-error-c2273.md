---
title: 編譯器錯誤 C2273 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2273
dev_langs:
- C++
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 995f75487820976d045e5db05fe2b170260240cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066213"
---
# <a name="compiler-error-c2273"></a>編譯器錯誤 C2273

'type'：當做 '->' 運算子的右邊不合法

類型會顯示為的右運算元`->`運算子。

此錯誤可能被因嘗試存取使用者定義型別轉換。 在 -> 與 `operator` 之間使用關鍵字 `type`。

下列範例會產生 C2273:

```
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