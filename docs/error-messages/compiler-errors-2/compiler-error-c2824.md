---
title: 編譯器錯誤 C2824
ms.date: 11/04/2016
f1_keywords:
- C2824
helpviewer_keywords:
- C2824
ms.assetid: 5bd865f7-e0af-404e-80fe-e2b798b44a59
ms.openlocfilehash: ee012d7244079fd881210eb969f4844a2c6e85d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750633"
---
# <a name="compiler-error-c2824"></a>編譯器錯誤 C2824

' operator new ' 的傳回類型必須是 ' void * '

使用非基底指標時，運算子 `new` 的多載必須傳回 `void *`。

下列範例會產生 C2824：

```cpp
// C2824.cpp
// compile with: /c
class   A {
   A* operator new(size_t i, char *m);   // C2824
   // try the following line instead
   // void* operator new(size_t i, char *m);
};
```
