---
title: 編譯器警告 (層級 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: c737a48883b97970af70014e2bda4bdc508ab471
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468675"
---
# <a name="compiler-warning-level-1-c4228"></a>編譯器警告 (層級 1) C4228

使用非標準擴充： 忽略宣告子清單中逗號後的限定詞

使用限定詞的要**const**或是`volatile`宣告變數時，逗號是 Microsoft 延伸模組之後 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>範例

```
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```