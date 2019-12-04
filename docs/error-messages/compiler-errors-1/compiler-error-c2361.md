---
title: 編譯器錯誤 C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: 747b85b57bee9e53f13a978254798a1dc268ef85
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759889"
---
# <a name="compiler-error-c2361"></a>編譯器錯誤 C2361

' identifier ' 的初始化已由 ' default ' 標籤略過

可以在 `switch` 語句中略過 `identifier` 的初始化。 除非宣告包含在區塊中，否則您無法跳過具有初始化運算式的宣告。 （除非在區塊內宣告，否則變數會在範圍內，直到 `switch` 語句結束為止）。

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

可能的解決方案：

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
