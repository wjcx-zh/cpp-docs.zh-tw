---
title: 編譯器警告 (層級 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 226bc91c272ff62ebe127aa190384d30a214b05d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223248"
---
# <a name="compiler-warning-level-1-c4218"></a>編譯器警告 (層級 1) C4218

使用非標準的擴充：必須指定至少一個儲存類別或類型

使用預設的 Microsoft 擴充功能（/Ze）時，您可以宣告變數，而不需要指定類型或儲存類別。 預設類型為 **`int`** 。

## <a name="example"></a>範例

```cpp
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

這類宣告在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下無效。
