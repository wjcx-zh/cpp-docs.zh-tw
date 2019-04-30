---
title: 編譯器錯誤 C3848
ms.date: 11/04/2016
f1_keywords:
- C3848
helpviewer_keywords:
- C3848
ms.assetid: 32d3ccef-01ec-4f8b-bbff-fb9b1a76b4c4
ms.openlocfilehash: 1d738311ada14999a5345a4e2394631254dda00a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380992"
---
# <a name="compiler-error-c3848"></a>編譯器錯誤 C3848

具有類型 'type' 的運算式會失去某些 const-volatile 限定詞才能呼叫 'function'

具有指定的常數 volatile 類型的變數只能呼叫成員函式定義包含大於或等於常數 volatile 限定性條件。

下列範例會產生 C3848:

```
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