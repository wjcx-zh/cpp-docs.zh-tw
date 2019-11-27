---
title: 編譯器警告 (層級 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: e15140bd2f0983bde64c89a054fd733d1ab902ac
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541858"
---
# <a name="compiler-warning-level-4-c4208"></a>編譯器警告 (層級 4) C4208

使用非標準的擴充： delete [exp]-exp 已評估但已忽略

使用 Microsoft extensions （/Ze）時，您可以使用括弧內的值搭配[delete 運算子](../../cpp/delete-operator-cpp.md)來刪除陣列。 此值會被忽略。

```cpp
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

這類值在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下是不正確。