---
title: 編譯器錯誤 C2793
ms.date: 11/04/2016
f1_keywords:
- C2793
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
ms.openlocfilehash: 5533a0e8f75a1a513fbabe451fb41629a4595382
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428180"
---
# <a name="compiler-error-c2793"></a>編譯器錯誤 C2793

'token': 非預期的語彙基元下列 ':: '，識別項或關鍵字 'operator' 必須是

唯一的權杖，可以遵循`__super::`是識別項或關鍵字`operator`。

下列範例會產生 C2793

```
// C2793.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::(); // C2793
   }
};
```