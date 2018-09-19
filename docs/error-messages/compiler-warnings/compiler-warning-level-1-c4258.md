---
title: 編譯器警告 （層級 1） C4258 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4258
dev_langs:
- C++
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4d9aacd6e3681a1eb42073df8a13d7ce72c5634
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083531"
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