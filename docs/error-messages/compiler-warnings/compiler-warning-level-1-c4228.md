---
title: 編譯器警告（層級1） C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: 75bd34a4338db7a430c1951d5bc3bd61dbce4f64
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627270"
---
# <a name="compiler-warning-level-1-c4228"></a>編譯器警告（層級1） C4228

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