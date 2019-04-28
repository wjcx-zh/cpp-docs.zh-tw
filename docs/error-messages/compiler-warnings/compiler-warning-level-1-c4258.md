---
title: 編譯器警告 (層級 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a3ce4c81a86920baddfc1b277df0236a96254be4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207392"
---
# <a name="compiler-warning-level-1-c4258"></a>編譯器警告 (層級 1) C4258

'variable': 定義與 for 迴圈會被忽略;自封閉範圍的定義使用 」

底下[/Ze](../../build/reference/za-ze-disable-language-extensions.md)並[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)中, 定義的變數[如](../../cpp/for-statement-cpp.md)迴圈超出範圍**的**迴圈結束。 如果迴圈變數，但在封入迴圈中，定義同名的變數會一次在包含的範圍，就會發生這個警告**針對**迴圈。 例如: 

```
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```