---
title: 編譯器錯誤 C2574
ms.date: 11/04/2016
f1_keywords:
- C2574
helpviewer_keywords:
- C2574
ms.assetid: 3e1c5c18-ee8b-4dbb-bfc0-d3b8991af71b
ms.openlocfilehash: 764ff36441c563edd538c41be5c23c12f80e2537
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604954"
---
# <a name="compiler-error-c2574"></a>編譯器錯誤 C2574

'解構函式': 不能宣告為 static

解構函式或建構函式都不可以宣告`static`。

下列範例會產生 C2574:

```
// C2574.cpp
// compile with: /c
class A {
   virtual static ~A();   // C2574
   //  try the following line instead
   // virtual ~A();
};
```