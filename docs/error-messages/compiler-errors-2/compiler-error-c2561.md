---
title: 編譯器錯誤 C2561 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8611af23ab884a853fc751ae82c636753993495b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070700"
---
# <a name="compiler-error-c2561"></a>編譯器錯誤 C2561

'identifier': 函式必須傳回值

此函式宣告為傳回值，但函式定義不包含`return`陳述式。

此錯誤可能被因不正確的函式原型：

1. 如果函式不會傳回值，以傳回型別來宣告函式[void](../../cpp/void-cpp.md)。

1. 請檢查所有可能的分支，函式的傳回類型在原型中宣告的值。

1. 包含存放區中的傳回值的內嵌組件常式的 c + + 函式`AX`註冊可能需要的 return 陳述式。 中的值複製`AX`給暫存變數，並從函式會傳回該變數。

下列範例會產生 C2561:

```
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```