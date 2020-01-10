---
title: 編譯器錯誤 C2511
ms.date: 11/04/2016
f1_keywords:
- C2511
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
ms.openlocfilehash: ff78cb50b274fe40d513739264bd7e9894bbed9d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746561"
---
# <a name="compiler-error-c2511"></a>編譯器錯誤 C2511

' identifier '：在 ' class ' 中找不到多載成員函式

未使用指定的參數宣告函式的任何版本。  可能的原因:

1. 傳遞了錯誤的參數給函數。

1. 以錯誤順序傳遞的參數。

1. 參數名稱的拼寫不正確。

下列範例會產生 C2511：

```cpp
// C2511.cpp
// compile with: /c
class C {
   int c_2;
   int Func(char *, char *);
};

int C::Func(char *, char *, int i) {   // C2511
// try the following line instead
// int C::Func(char *, char *) {
   return 0;
}
```
