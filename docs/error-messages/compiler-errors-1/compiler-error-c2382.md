---
title: 編譯器錯誤 C2382 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2382
dev_langs:
- C++
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc54ef088cf756918abe385acd3e5bed6b856a8a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085793"
---
# <a name="compiler-error-c2382"></a>編譯器錯誤 C2382

'function'：重複定義; 不同的例外狀況規格

在 [/Za](../../build/reference/za-ze-disable-language-extensions.md)下，此錯誤表示嘗試只在 [例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)執行函式多載。

下列範例會產生 C2382：

```
// C2382.cpp
// compile with: /Za /c
void f1(void) throw(int) {}
void f1(void) throw(char) {}   // C2382
void f2(void) throw(char) {}   // OK
```