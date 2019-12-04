---
title: 編譯器錯誤 C2459
ms.date: 11/04/2016
f1_keywords:
- C2459
helpviewer_keywords:
- C2459
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
ms.openlocfilehash: c49c348968f750c7e5c64ab9ef4f298d3fc74f67
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743987"
---
# <a name="compiler-error-c2459"></a>編譯器錯誤 C2459

' identifier '：正在定義;無法新增為匿名成員

類別、結構或等位會由匿名等位的成員在其本身的範圍中重新定義。

下列範例會產生 C2459：

```cpp
// C2459.cpp
// compile with: /c
class C {
   union { int C; };   // C2459
   union { int D; };
};
```
