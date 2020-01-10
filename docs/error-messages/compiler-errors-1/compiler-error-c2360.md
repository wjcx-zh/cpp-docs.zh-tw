---
title: 編譯器錯誤 C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 226fcd8a27c9abdb789b8191a5cf4e59cc4a66cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759902"
---
# <a name="compiler-error-c2360"></a>編譯器錯誤 C2360

' identifier ' 的初始化已由 ' case ' 標籤略過

可以在 `switch` 語句中略過 `identifier` 的初始化。 除非宣告包含在區塊中，否則您無法跳過具有初始化運算式的宣告。 （除非在區塊內宣告，否則變數會在範圍內，直到 `switch` 語句結束為止）。

下列範例會產生 C2360：

```cpp
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

可能的解決方案：

```cpp
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```
