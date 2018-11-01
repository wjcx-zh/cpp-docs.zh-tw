---
title: 編譯器錯誤 C2148
ms.date: 11/04/2016
f1_keywords:
- C2148
helpviewer_keywords:
- C2148
ms.assetid: e510c2c9-7b57-4ce8-be03-ba363e2cc5d9
ms.openlocfilehash: 893f1f029b2ea1aaf7ff53a5ee5cee7fcbe36e7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440348"
---
# <a name="compiler-error-c2148"></a>編譯器錯誤 C2148

陣列的大小總計不得超過 0x7fffffff 位元組

陣列超過限制。 減少陣列大小。

## <a name="example"></a>範例

下列範例會產生 C2148:

```
// C2148.cpp
#include <stdio.h>
#include <stdlib.h>

int main( ) {
   char MyArray[0x7ffffffff];   // C2148
   char * MyArray2 = (char *)malloc(0x7fffffff);

   if (MyArray2)
      printf_s("It worked!");
   else
      printf_s("It didn't work.");
}
```