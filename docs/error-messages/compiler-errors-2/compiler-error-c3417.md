---
title: 編譯器錯誤 C3417
ms.date: 11/04/2016
f1_keywords:
- C3417
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
ms.openlocfilehash: 93f287dd7173cc83a8c910d035f80a15c6a4f701
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756158"
---
# <a name="compiler-error-c3417"></a>編譯器錯誤 C3417

' member '：實數值型別不能包含使用者定義的特殊成員函式

實值型別不能包含函式，例如預設實例的「函數」、「析構函數」或「複製」。

下列範例會產生 C3517：

```cpp
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```
