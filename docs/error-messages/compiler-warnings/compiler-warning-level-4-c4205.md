---
title: 編譯器警告 (層級 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 1b165d2bdb2fb50df89fdd77c734c054a40b6e95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401224"
---
# <a name="compiler-warning-level-4-c4205"></a>編譯器警告 (層級 4) C4205

使用非標準擴充： 函式範圍中的靜態函式宣告

使用 Microsoft 擴充功能 (/Ze) 下**靜態**函式可以在另一個函式內宣告。 此函式有全域範圍。

## <a name="example"></a>範例

```
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

這類初始化是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。