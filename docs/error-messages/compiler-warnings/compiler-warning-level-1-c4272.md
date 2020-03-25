---
title: 編譯器警告 (層級 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 747b9e60ad2b8b0036c6eac50d44c2d70277384f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163119"
---
# <a name="compiler-warning-level-1-c4272"></a>編譯器警告 (層級 1) C4272

' function '：標記為 __declspec （dllimport）;匯入函數時，必須指定原生呼叫慣例。

匯出以[__clrcall](../../cpp/clrcall.md)呼叫慣例標記的函式是錯誤的，如果您嘗試匯入標記為 `__clrcall`的函數，編譯器會發出此警告。

下列範例會產生 C4272：

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```
