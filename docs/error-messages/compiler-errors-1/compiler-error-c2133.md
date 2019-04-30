---
title: 編譯器錯誤 C2133
ms.date: 11/04/2016
f1_keywords:
- C2133
helpviewer_keywords:
- C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
ms.openlocfilehash: 68672ae76024d3d09d738d997c485a3205c7dd2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397571"
---
# <a name="compiler-error-c2133"></a>編譯器錯誤 C2133

'identifier': 未知的大小

可變大小的陣列宣告為類別、 結構、 等位或列舉的成員。 /Za (ANSI C) 選項不允許成員可變大小的陣列。

下列範例會產生 C2133:

```
// C2133.cpp
// compile with: /Za
struct X {
   int a[0];   // C2133 unsized array
};
```

可能的解決方式：

```
// C2133b.cpp
// compile with: /c
struct X {
   int a[0];   // no /Za
};
```