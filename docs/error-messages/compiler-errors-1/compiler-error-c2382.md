---
title: 編譯器錯誤 C2382
ms.date: 11/04/2016
f1_keywords:
- C2382
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
ms.openlocfilehash: 8b623d292998960052ff5d6978d8c12ae7f3fb32
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745365"
---
# <a name="compiler-error-c2382"></a>編譯器錯誤 C2382

'function'：重複定義; 不同的例外狀況規格

在 [/Za](../../build/reference/za-ze-disable-language-extensions.md)下，此錯誤表示嘗試只在 [例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)執行函式多載。

下列範例會產生 C2382：

```cpp
// C2382.cpp
// compile with: /Za /c
void f1(void) throw(int) {}
void f1(void) throw(char) {}   // C2382
void f2(void) throw(char) {}   // OK
```
