---
title: 編譯器警告 (層級 4) C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: 45ed4817dbf2c7ecd63cd0c669d6e1cf768184bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174046"
---
# <a name="compiler-warning-level-4-c4204"></a>編譯器警告 (層級 4) C4204

使用非標準的擴充：非常數匯總初始化運算式

使用 Microsoft extensions （/Ze）時，您可以使用非常數的值來初始化匯總類型（陣列、結構、等位和類別）。

## <a name="example"></a>範例

```c
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

這類初始化在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下無效。
