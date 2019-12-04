---
title: 編譯器錯誤 C3923
ms.date: 11/04/2016
f1_keywords:
- C3923
helpviewer_keywords:
- C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
ms.openlocfilehash: e688afcfd477ce88c437f22f864bfb97b1d2ade1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757770"
---
# <a name="compiler-error-c3923"></a>編譯器錯誤 C3923

'member'：WinRT 或 Managed 類別的成員函式中不允許有區域類別、結構或等位定義

## <a name="example"></a>範例

下列範例會產生 C3923。

```cpp
// C3923.cpp
// compile with: /clr /c
ref struct x {
   void Test() {
      struct a {};   // C3923
      class b {};   // C3923
      union c {};   // C3923
   }
};
```
