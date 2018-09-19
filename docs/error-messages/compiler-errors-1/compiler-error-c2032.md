---
title: 編譯器錯誤 C2032 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ab02ca695ec94f25054e3490232b782a46a53a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064005"
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