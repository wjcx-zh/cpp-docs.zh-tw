---
title: 編譯器警告 （層級 3） C4645 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4645
dev_langs:
- C++
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b597678e726d6b10240c442ed7e48698a993e2fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046533"
---
# <a name="compiler-warning-level-3-c4645"></a>編譯器警告 (層級 3) C4645

使用 __declspec(noreturn) 宣告的函式有傳回的陳述式

A[會傳回](../../cpp/return-statement-in-program-termination-cpp.md)標示為函式中找不到陳述式[noreturn](../../cpp/noreturn.md) `__declspec`修飾詞。 已忽略 `return` 陳述式。

下列範例會產生 C4645：

```
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```