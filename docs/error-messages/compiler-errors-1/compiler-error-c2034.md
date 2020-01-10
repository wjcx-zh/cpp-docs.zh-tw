---
title: 編譯器錯誤 C2034
ms.date: 11/04/2016
f1_keywords:
- C2034
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
ms.openlocfilehash: c416c833edf522e4e67cf84aaf7fc945ee8a7972
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755105"
---
# <a name="compiler-error-c2034"></a>編譯器錯誤 C2034

' identifier '：位欄位的類型對位數而言太小

位欄位宣告中的位數超過基底類型的大小。

下列範例會產生 C2034：

```cpp
// C2034.cpp
struct A {
   char test : 9;   // C2034, char has 8 bits
};
```

可能的解決方案：

```cpp
// C2034b.cpp
// compile with: /c
struct A {
   char test : 8;
};
```
