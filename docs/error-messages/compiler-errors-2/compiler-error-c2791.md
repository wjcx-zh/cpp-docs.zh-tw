---
title: 編譯器錯誤 C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: d589094f117135474d1a8788867d2d571bbb5f5d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739541"
---
# <a name="compiler-error-c2791"></a>編譯器錯誤 C2791

' super ' 的使用不合法： ' class ' 沒有任何基類

在沒有任何基類的類別的成員函式內容中，使用了關鍵字[super](../../cpp/super.md) 。

下列範例會產生 C2791：

```cpp
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```
