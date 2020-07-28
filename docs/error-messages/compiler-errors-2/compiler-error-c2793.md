---
title: 編譯器錯誤 C2793
ms.date: 11/04/2016
f1_keywords:
- C2793
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
ms.openlocfilehash: faf87334f1a98661078341a4d7dc11280802a376
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220206"
---
# <a name="compiler-error-c2793"></a>編譯器錯誤 C2793

' token '：必須是 '：： ' 後面的非預期的標記，必須是識別碼或關鍵字 ' operator '

唯一可以遵循的 token `__super::` 是 identifier 或關鍵字 **`operator`** 。

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
