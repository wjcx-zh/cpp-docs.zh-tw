---
title: 編譯器錯誤 C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: b4a14be9cd32c752e2ab889417494e80b935e31b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755560"
---
# <a name="compiler-error-c2561"></a>編譯器錯誤 C2561

' identifier '：函式必須傳回值

函式已宣告為傳回值，但函式定義未包含 `return` 語句。

此錯誤可能是由不正確的函數原型所造成：

1. 如果函式未傳回值，請宣告具有[void](../../cpp/void-cpp.md)傳回類型的函數。

1. 檢查函式的所有可能分支是否都會傳回原型中宣告之類型的值。

1. C++包含將傳回值儲存在 `AX` 暫存器中之內嵌組解碼常式的函數，可能需要 return 語句。 將 `AX` 中的值複製到暫存變數，並從函式傳回該變數。

下列範例會產生 C2561：

```cpp
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
