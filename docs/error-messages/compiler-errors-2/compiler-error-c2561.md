---
title: 編譯器錯誤 C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 9c42a2da662a286f3e6887f6a1dba381687136bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206961"
---
# <a name="compiler-error-c2561"></a>編譯器錯誤 C2561

' identifier '：函式必須傳回值

函式已宣告為傳回值，但函式定義未包含 **`return`** 語句。

此錯誤可能是由不正確的函數原型所造成：

1. 如果函式未傳回值，請宣告具有[void](../../cpp/void-cpp.md)傳回類型的函數。

1. 檢查函式的所有可能分支是否都會傳回原型中宣告之類型的值。

1. 包含將傳回值儲存在暫存器中之內嵌組解碼常式的 c + + 函式， `AX` 可能需要 return 語句。 將中的值複製 `AX` 到暫存變數，並從函式傳回該變數。

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
