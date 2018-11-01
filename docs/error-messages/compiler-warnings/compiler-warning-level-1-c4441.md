---
title: 編譯器警告 (層級 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: 45d7a6af09677c1e63dab5ffcc55c35d8203b40b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539690"
---
# <a name="compiler-warning-level-1-c4441"></a>編譯器警告 (層級 1) C4441

呼叫慣例 'cc1' 忽略;改用 ' cc2'

在 受管理的使用者定義型別和全域函式的泛型成員函式必須使用[__clrcall](../../cpp/clrcall.md)呼叫慣例。  使用編譯器`__clrcall`。

## <a name="example"></a>範例

下列範例會產生 C4441。

```
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```