---
title: 編譯器錯誤 C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 6e956ccb021dc3bce4d107e4aa6e0bbe4356283b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364723"
---
# <a name="compiler-error-c2360"></a>編譯器錯誤 C2360

'identifier' 的初始化會被 'case' 標籤略過

初始化`identifier`中就可以略過`switch`陳述式。 除非宣告括在區塊中，您不能跳過的初始設定式的宣告。 (結尾除非它被宣告區塊內，變數是範圍內`switch`陳述式。)

下列範例會產生 C2360:

```
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

```
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