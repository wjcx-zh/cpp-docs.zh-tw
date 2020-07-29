---
title: 編譯器錯誤 C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: 7efc94cc859bbee6db0ce973135c7501fd79ae1d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206935"
---
# <a name="compiler-error-c2562"></a>編譯器錯誤 C2562

' identifier '： ' void ' 函式傳回值

函式會宣告為，但會傳回 **`void`** 值。

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
