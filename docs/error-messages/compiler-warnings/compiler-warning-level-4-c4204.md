---
title: 編譯器警告 (層級 4) C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: e16cb9fb59ee6ec24bb9b68dad1be9432d9eee3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401237"
---
# <a name="compiler-warning-level-4-c4204"></a>編譯器警告 (層級 4) C4204

使用非標準擴充： 非常數的彙總初始設定式

使用 Microsoft 擴充功能 (/Ze)，您可以初始化彙總類型 （陣列、 結構、 等位和類別），且不是常數的值。

## <a name="example"></a>範例

```
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

這類初始化是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。