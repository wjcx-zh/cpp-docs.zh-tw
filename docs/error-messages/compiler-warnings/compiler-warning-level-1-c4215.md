---
title: 編譯器警告 (層級 1) C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: aeab5a90647015a8848d7c2af62f7d7fc6932900
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223274"
---
# <a name="compiler-warning-level-1-c4215"></a>編譯器警告 (層級 1) C4215

使用非標準的擴充： long float

預設的 Microsoft extensions （/Ze）會將**long float**視為 **`double`** 。 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）則不會。 使用 **`double`** 來維護相容性。

下列範例會產生 C4215：

```cpp
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```
