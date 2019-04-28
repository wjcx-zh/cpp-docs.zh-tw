---
title: 編譯器錯誤 C2658
ms.date: 11/04/2016
f1_keywords:
- C2658
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
ms.openlocfilehash: 792fd497ad7cdb98ae72f3e6451780dad487624d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360407"
---
# <a name="compiler-error-c2658"></a>編譯器錯誤 C2658

'member': 匿名結構/等位中的重複定義

兩個匿名結構或等位包含具有相同的識別項，但具有不同類型的成員宣告。 底下[/Za](../../build/reference/za-ze-disable-language-extensions.md)，您也會具有相同的識別項和類型成員取得這項錯誤。

下列範例會產生 C2658:

```
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