---
title: 編譯器錯誤 C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: b95c6459c0ff093d22f3e754f2c7fd6564d2b296
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221194"
---
# <a name="compiler-error-c2361"></a>編譯器錯誤 C2361

' identifier ' 的初始化已由 ' default ' 標籤略過

`identifier`可以在語句中略過的初始化 **`switch`** 。 除非宣告包含在區塊中，否則您無法跳過具有初始化運算式的宣告。 （除非在區塊內宣告，否則變數會在範圍內，直到語句結束為止 **`switch`** ）。

下列範例會產生 C2361：

```cpp
// C2361.cpp
void func( void ) {
   int x;
   switch (x) {
   case 0 :
      int i = 1;
      { int j = 1; }
   default :   // C2361 error
      int k = 1;
   }
}
```

可能的解決方式：

```cpp
// C2361b.cpp
// compile with: /c
void func( void ) {
   int x = 0;
   switch (x) {
   case 0 :
      { int j = 1; int i = 1;}
   default :
      int k = 1;
   }
}
```
