---
title: 編譯器警告 (層級 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a192fb9d8dc046bb3493b90b85371175520ccf95
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230723"
---
# <a name="compiler-warning-level-1-c4258"></a>編譯器警告 (層級 1) C4258

' variable '：已忽略 for 迴圈中的定義;會使用來自封閉範圍的定義 "

在[/ze](../../build/reference/za-ze-disable-language-extensions.md)和[/zc： forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)底下，在[for](../../cpp/for-statement-cpp.md)迴圈中定義的變數會在迴圈結束之後移出範圍 **`for`** 。 如果變數的名稱與迴圈變數同名，但在封閉迴圈中定義，則會在包含迴圈的範圍中再次使用 **`for`** 。 例如：

```cpp
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
