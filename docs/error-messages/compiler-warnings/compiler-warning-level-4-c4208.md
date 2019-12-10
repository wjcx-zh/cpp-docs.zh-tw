---
title: 編譯器警告 (層級 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: c6e83feacd08bdb2203873a14a47ebde686a94f9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991603"
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
