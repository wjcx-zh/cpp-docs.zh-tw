---
title: 編譯器錯誤 C2523
ms.date: 11/04/2016
f1_keywords:
- C2523
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
ms.openlocfilehash: 56b0f88949d7a7fa5af945ab5d03ee9a480d6d3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746418"
---
# <a name="compiler-error-c2523"></a>編譯器錯誤 C2523

' class：： ~ identifier '：析構器/完成項標記不相符

函式的名稱必須是類別名稱，前面加上波狀符號（`~`）。 此函式和析構函數是唯一與類別同名的成員。

下列範例會產生 C2523：

```cpp
// C2523.cpp
// compile with: /c
class A {
   ~B();    // C2523
   ~A();   // OK
};
```
