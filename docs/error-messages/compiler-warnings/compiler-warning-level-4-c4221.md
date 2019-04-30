---
title: 編譯器警告 (層級 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: f552a5d76d1a778cdf72cbe079138f609350ffb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401094"
---
# <a name="compiler-warning-level-4-c4221"></a>編譯器警告 (層級 4) C4221

使用非標準擴充: 'identifier': 不可以使用 自動變數的位址初始化

使用預設的 Microsoft 擴充功能 (/Ze) 中，您可以初始化彙總類型 (**陣列**， `struct`，或**union**) （自動） 的區域變數的位址。

## <a name="example"></a>範例

```
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

這類初始化是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。