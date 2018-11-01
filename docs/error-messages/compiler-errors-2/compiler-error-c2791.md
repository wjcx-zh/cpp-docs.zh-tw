---
title: 編譯器錯誤 C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: 66a111ea6fe2ca5acfbc473d19da62d9de67372a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666605"
---
# <a name="compiler-error-c2791"></a>編譯器錯誤 C2791

不合法使用 'super': 'class' 沒有任何基底類別

關鍵字[super](../../cpp/super.md)並沒有任何基底類別的類別的成員函式的內容中使用。

下列範例會產生 C2791:

```
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```