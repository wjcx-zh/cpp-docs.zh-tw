---
title: 編譯器警告 (層級 4) C4932
description: 描述 Microsoft C/c + + 編譯器警告 C4932。
ms.date: 08/25/2020
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: ece2ae14fd8e1198a97f5e772fcce52c47464878
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898291"
---
# <a name="compiler-warning-level-4-c4932"></a>編譯器警告 (層級 4) C4932

> `__identifier(identifier_1)` 而且 `__identifier(identifier_2)` 是不區分的

編譯器無法區分 **`_finally`** 和 **`__finally`** 或，以及做為 **`__try`** **`_try`** 傳遞給的參數 [`__identifier`](../../extensions/identifier-cpp-cli.md) 。 您不應該嘗試同時使用它們作為相同程式中的識別項，因為它會導致 [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) 錯誤。

下列範例會產生 C4932：

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
