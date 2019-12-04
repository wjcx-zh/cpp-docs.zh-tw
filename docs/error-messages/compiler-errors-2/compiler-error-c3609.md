---
title: 編譯器錯誤 C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 1d3078614ff6818dd4185b3bd5ed2f49413db16f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755950"
---
# <a name="compiler-error-c3609"></a>編譯器錯誤 C3609

'member'：密封或最終函式必須為虛擬

只有標記為 `virtual`的類別、結構或成員函式才允許[sealed](../../extensions/sealed-cpp-component-extensions.md)和[final](../../cpp/final-specifier.md)關鍵字。

下列範例會產生 C3609：

```cpp
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
