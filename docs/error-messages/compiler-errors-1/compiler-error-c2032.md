---
title: 編譯器錯誤 C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: d20bc61df2d0bab9115768b3bc0589f11a9bcdb9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302090"
---
# <a name="compiler-error-c2032"></a>編譯器錯誤 C2032

' identifier '：函式不可以是結構/聯集 ' structorunion ' 的成員

結構或等位具有成員函式，但不允許在C++ C 中使用。若要解決此錯誤，請將編譯C++為程式或移除成員函式。

下列範例會產生 C2032：

```c
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

可能的解決方案：

```c
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```
