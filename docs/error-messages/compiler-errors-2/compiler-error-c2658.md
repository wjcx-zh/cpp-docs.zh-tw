---
title: 編譯器錯誤 C2658
ms.date: 11/04/2016
f1_keywords:
- C2658
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
ms.openlocfilehash: 77a9122d20561ceee4f211394b3b81900d5580ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756080"
---
# <a name="compiler-error-c2658"></a>編譯器錯誤 C2658

' member '：在匿名結構/等位中重新定義

兩個匿名結構或等位包含具有相同識別碼但具有不同類型的成員宣告。 在[/za](../../build/reference/za-ze-disable-language-extensions.md)下，您也會收到具有相同識別碼和類型之成員的這個錯誤。

下列範例會產生 C2658：

```cpp
// C2658.cpp
// compile with: /c
struct X {
   union { // can be struct too
      int i;
   };
   union {
      int i;   // Under /Za, C2658
      // int i not needed here because it is defined in the first union
   };
};

struct Z {
   union {
      char *i;
   };

   union {
      void *i;   // C2658 redefinition of 'i'
      // try the following line instead
      // void *ii;
   };
};
```
