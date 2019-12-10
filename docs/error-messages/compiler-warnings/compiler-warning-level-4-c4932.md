---
title: 編譯器警告 (層級 4) C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: dd1db3cccf9f1b24f82ddddf10fcf35f39a9251a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988785"
---
# <a name="compiler-warning-level-4-c4932"></a>編譯器警告 (層級 4) C4932

__identifier （識別碼）和 \__identifier （identifier）無法區分

編譯器無法區分作為參數傳遞給 **__identifier** 的 `__finally` _finally `__try` 與 **或** 與 [_try](../../extensions/identifier-cpp-cli.md)。 您不應該嘗試同時使用它們作為相同程式中的識別項，因為它會導致 [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) 錯誤。

下列範例會產生 C4932：

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
