---
title: 編譯器錯誤 C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 8350c5baf129b88c178be280d2da7fe856c6cf57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517607"
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