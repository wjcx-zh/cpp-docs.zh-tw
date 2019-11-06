---
title: 編譯器警告（層級1） C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 13c56c2261cd069e7edec63921c198e2bee56c95
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626690"
---
# <a name="compiler-warning-level-1-c4272"></a>編譯器警告（層級1） C4272

' function '：標記為 __declspec （dllimport）;匯入函數時，必須指定原生呼叫慣例。

匯出以[__clrcall](../../cpp/clrcall.md)呼叫慣例標記的函式是錯誤的，如果您嘗試匯入標記為 `__clrcall`的函數，編譯器會發出此警告。

下列範例會產生 C4272：

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```