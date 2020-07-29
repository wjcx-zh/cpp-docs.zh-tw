---
title: 編譯器錯誤 C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: a2a164f919dc7535a4587d51f4f7dba8653a1760
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214681"
---
# <a name="compiler-error-c2360"></a>編譯器錯誤 C2360

' identifier ' 的初始化已由 ' case ' 標籤略過

`identifier`可以在語句中略過的初始化 **`switch`** 。 除非宣告包含在區塊中，否則您無法跳過具有初始化運算式的宣告。 （除非在區塊內宣告，否則變數會在範圍內，直到語句結束為止 **`switch`** ）。

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

可能的解決方式：

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
