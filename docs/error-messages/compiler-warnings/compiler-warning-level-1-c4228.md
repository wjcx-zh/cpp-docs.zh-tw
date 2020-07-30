---
title: 編譯器警告 (層級 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: 3a89d5c0924e6fd12a4ccf8afa957f8908670d49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223235"
---
# <a name="compiler-warning-level-1-c4228"></a>編譯器警告 (層級 1) C4228

使用非標準的延伸模組：忽略宣告子清單中逗號之後的限定詞

**`const`** **`volatile`** 當宣告變數是 Microsoft 擴充功能（[/ze](../../build/reference/za-ze-disable-language-extensions.md)）時，使用逗點或逗號之後的限定詞。

## <a name="example"></a>範例

```cpp
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```
