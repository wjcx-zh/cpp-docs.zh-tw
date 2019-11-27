---
title: 編譯器警告 (層級 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: fa87c240472df2926753781f0f14cbd69752de00
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541931"
---
# <a name="compiler-warning-level-4-c4221"></a>編譯器警告 (層級 4) C4221

使用非標準的擴充： ' identifier '：無法使用自動變數的位址初始化

使用預設的 Microsoft 擴充功能（/Ze）時，您可以使用本機（自動）變數的位址來初始化匯總類型（**陣列**、 **`struct`或等**位）。

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