---
title: 編譯器錯誤 C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: 78536fdc0c2a6a6e9c4842fdea6423037496b30b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755547"
---
# <a name="compiler-error-c2562"></a>編譯器錯誤 C2562

' identifier '： ' void ' 函式傳回值

函式會宣告為 `void`，但會傳回值。

此錯誤可能是由不正確的函數原型所造成。

如果您在函式宣告中指定傳回型別，就可以修正這個錯誤。

下列範例會產生 C2562：

```cpp
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```
