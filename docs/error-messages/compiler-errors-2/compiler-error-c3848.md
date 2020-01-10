---
title: 編譯器錯誤 C3848
ms.date: 11/04/2016
f1_keywords:
- C3848
helpviewer_keywords:
- C3848
ms.assetid: 32d3ccef-01ec-4f8b-bbff-fb9b1a76b4c4
ms.openlocfilehash: 51a5cf6d866a5e5ee914a3d70365761749f79eea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761942"
---
# <a name="compiler-error-c3848"></a>編譯器錯誤 C3848

具有類型 ' type ' 的運算式會遺失某些 const volatile 限定詞，以便呼叫 ' function '

具有指定之 const volatile 類型的變數只能呼叫以相同或更大的 const volatile 條件限定定義的成員函式。

下列範例會產生 C3848：

```cpp
// C3848.cpp
void glbFunc1()
{
}

typedef void (* pFunc1)();

struct S3
{
   operator pFunc1() // const
   {
      return &glbFunc1;
   }
};

int main()
{
   const S3 s3;
   s3();   // C3848, uncomment const qualifier
}
```
