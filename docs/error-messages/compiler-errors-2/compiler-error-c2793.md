---
title: 編譯器錯誤 C2793
ms.date: 11/04/2016
f1_keywords:
- C2793
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
ms.openlocfilehash: 5b8712473631b16e2bbb47430966ccc0c552b9df
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739385"
---
# <a name="compiler-error-c2793"></a>編譯器錯誤 C2793

' token '：必須是 '：： ' 後面的非預期的標記，必須是識別碼或關鍵字 ' operator '

唯一可以遵循 `__super::` 的權杖是識別碼或關鍵字 `operator`。

下列範例會產生 C2793

```cpp
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
