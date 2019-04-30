---
title: 編譯器錯誤 C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: 5743aba880f23d7706940936fc4a3a1973a84ca1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400509"
---
# <a name="compiler-error-c2032"></a>編譯器錯誤 C2032

'identifier': 不可的結構/等位 'structorunion' 的成員函式。

結構或等位有成員函式，這允許在C++而不是在 c。若要解決此錯誤，請編譯成C++程式，或移除此成員函式。

下列範例會產生 C2032:

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

可能的解決方式：

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```