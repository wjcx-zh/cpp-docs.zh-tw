---
title: 編譯器錯誤 C2133
ms.date: 11/04/2016
f1_keywords:
- C2133
helpviewer_keywords:
- C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
ms.openlocfilehash: b51b556ea576e02b85a5c2ee5032909af39c7b2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758433"
---
# <a name="compiler-error-c2133"></a>編譯器錯誤 C2133

' identifier '：未知的大小

可變大小陣列會宣告為類別、結構、等位或列舉的成員。 /Za （ANSI C）選項不允許可變大小成員陣列。

下列範例會產生 C2133：

```cpp
// C2133.cpp
// compile with: /Za
struct X {
   int a[0];   // C2133 unsized array
};
```

可能的解決方案：

```cpp
// C2133b.cpp
// compile with: /c
struct X {
   int a[0];   // no /Za
};
```
