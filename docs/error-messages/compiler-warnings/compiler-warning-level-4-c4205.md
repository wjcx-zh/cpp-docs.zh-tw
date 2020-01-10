---
title: 編譯器警告 (層級 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: e46642494e55769a0676f0e33af0ca40c31939ad
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541793"
---
# <a name="compiler-warning-level-4-c4205"></a>編譯器警告 (層級 4) C4205

使用非標準的擴充：函式範圍中的靜態函式宣告

使用 Microsoft 擴充功能（/Ze）時，可以在另一個函式內宣告**靜態**函式。 函式會獲得全域範圍。

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