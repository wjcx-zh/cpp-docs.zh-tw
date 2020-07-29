---
title: 編譯器警告 (層級 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 6e85d4b6382f8d3811585bcf887c08694b86b71a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225263"
---
# <a name="compiler-warning-level-4-c4205"></a>編譯器警告 (層級 4) C4205

使用非標準的擴充：函式範圍中的靜態函式宣告

使用 Microsoft 擴充功能（/Ze）時， **`static`** 可以在另一個函式內宣告函式。 函式會獲得全域範圍。

## <a name="example"></a>範例

```c
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

這類初始化在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下無效。
