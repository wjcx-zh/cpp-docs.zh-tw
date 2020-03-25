---
title: 編譯器警告 (層級 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: c216143f2b47148f73502c847175201ea9a74fee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175892"
---
# <a name="compiler-warning-level-1-c4228"></a>編譯器警告 (層級 1) C4228

使用非標準的延伸模組：忽略宣告子清單中逗號之後的限定詞

當宣告變數是 Microsoft 擴充功能（[/ze](../../build/reference/za-ze-disable-language-extensions.md)）時，使用**const**或 `volatile` 之類的限定詞。

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
