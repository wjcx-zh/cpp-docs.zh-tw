---
title: 編譯器警告（層級1） C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 4000ba2254c868bf9959a6f0fb6f8e76255f7590
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966074"
---
# <a name="compiler-warning-level-1-c4313"></a>編譯器警告（層級1） C4313

'function': 格式字串中的 'format specifier' 與引數數目 (屬於類型 'type') 衝突

指定的格式與您所傳遞的值之間沒有衝突。 例如，您傳遞 64 位元的參數至未限定的 %d 格式規範，但其預期的是 32 位元的整數參數。 當程式碼是針對 64 位元目標編譯時，這個警告才有效。

## <a name="example"></a>範例

使用 64 位元目標編譯時，下列程式碼範例會產生 C4313。

```cpp
// C4313.cpp
// Compile by using: cl /W1 C4313.cpp
#include <stdio.h>
int main() {
   int * pI = 0;
   printf("%d", pI);   // C4313 on 64-bit platform code
   // Try one of the following lines instead:
   // printf("%p\n", pI);
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information
}
```