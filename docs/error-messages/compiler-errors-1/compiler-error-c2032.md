---
title: 編譯器錯誤 C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: 5743aba880f23d7706940936fc4a3a1973a84ca1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558245"
---
# <a name="compiler-error-c2032"></a>編譯器錯誤 C2032

'identifier': 不可的結構/等位 'structorunion' 的成員函式。

結構或等位具有 c + + 中，但在 c 中不允許成員函式若要解決此錯誤，編譯成 c + + 程式或是移除此成員函式。

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