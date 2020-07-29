---
title: 編譯器警告 (層級 4) C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: 992e047f31e4a30edd29ba6110bf119d2bc8928b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230593"
---
# <a name="compiler-warning-level-4-c4932"></a>編譯器警告 (層級 4) C4932

__identifier （識別碼）和 \_ _identifier （識別碼）無法區分

編譯器無法區分 **_finally**和 **`__finally`** 或 `__try` ， **_try**做為傳遞給[__identifier](../../extensions/identifier-cpp-cli.md)的參數。 您不應該嘗試同時使用它們作為相同程式中的識別項，因為它會導致 [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) 錯誤。

下列範例會產生 C4932：

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
