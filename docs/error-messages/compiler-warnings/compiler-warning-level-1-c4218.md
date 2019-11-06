---
title: 編譯器警告（層級1） C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f1db3eabc3b614019676dc4494e83104c62fe579
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627313"
---
# <a name="compiler-warning-level-1-c4218"></a>編譯器警告（層級1） C4218

使用非標準的擴充：必須指定至少一個儲存類別或類型

使用預設的 Microsoft 擴充功能（/Ze）時，您可以宣告變數，而不需要指定類型或儲存類別。 預設類型為 `int`。

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