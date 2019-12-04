---
title: 編譯器錯誤 C2617
ms.date: 11/04/2016
f1_keywords:
- C2617
helpviewer_keywords:
- C2617
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
ms.openlocfilehash: 60dd4e7de083bc4258eb7289d7b1c90d90871655
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754780"
---
# <a name="compiler-error-c2617"></a>編譯器錯誤 C2617

' function '：不一致的 return 語句

指定的函式沒有宣告的傳回型別，而先前的 return 語句並未提供值。

下列範例會產生 C2617：

```cpp
// C2617.cpp
int i;
func() {   // no return type prototype
   if( i ) return;   // no return value
   else return( 1 );   // C2617 detected on this line
}
```

可能的解決方案：

```cpp
// C2617b.cpp
// compile with: /c
int i;
int MyF() {
   if (i)
      return 0;
   else
      return (1);
}
```
