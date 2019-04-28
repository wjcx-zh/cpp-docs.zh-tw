---
title: 編譯器警告 (層級 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 26e136aa395729d520f4a71a06b6dc212cf21f8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208307"
---
# <a name="compiler-warning-level-1-c4272"></a>編譯器警告 (層級 1) C4272

'function': 標示為 __declspec （dllimport）;匯入函式時，必須指定原生呼叫慣例。

它是匯出函式標示為錯誤[__clrcall](../../cpp/clrcall.md)呼叫慣例和編譯器發出這個警告，如果您嘗試匯入標記為函式`__clrcall`。

下列範例會產生 C4272:

```
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```