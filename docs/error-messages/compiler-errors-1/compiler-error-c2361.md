---
title: 編譯器錯誤 C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: ca03a42cbf746a1ef32d9c79c23de637f05b56fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364359"
---
# <a name="compiler-error-c2361"></a>編譯器錯誤 C2361

'identifier' 的初始化會被 'default' 標籤略過

初始化`identifier`中就可以略過`switch`陳述式。 除非宣告括在區塊中，您不能跳過的初始設定式的宣告。 (結尾除非它被宣告區塊內，變數是範圍內`switch`陳述式。)

下列範例會產生 C2361:

```
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

```
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