---
title: 編譯器警告 (層級 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: e925f315e8506453403b0a0eda75b7c2956cc05c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219933"
---
# <a name="compiler-warning-level-4-c4221"></a>編譯器警告 (層級 4) C4221

使用非標準的擴充： ' identifier '：無法使用自動變數的位址初始化

使用預設的 Microsoft 擴充功能（/Ze）時，您可以**array** **`struct`** **`union`** 使用本機（自動）變數的位址來初始化匯總類型（陣列、或）。

## <a name="example"></a>範例

```c
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

這類初始化在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下無效。
