---
title: 編譯器錯誤 C2809
ms.date: 11/04/2016
f1_keywords:
- C2809
helpviewer_keywords:
- C2809
ms.assetid: ce796b8e-1a8c-4074-995d-1ad09afd0e93
ms.openlocfilehash: 04f875d4ff32cfad425be5bb28bea8ef92c508eb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758992"
---
# <a name="compiler-error-c2809"></a>編譯器錯誤 C2809

' operator operator ' 沒有型式參數

運算子缺少必要的參數。

下列範例會產生 C2809：

```cpp
// C2809.cpp
// compile with: /c
class A{};
int operator+ ();   // C2809
int operator+ (A);   // OK
```
