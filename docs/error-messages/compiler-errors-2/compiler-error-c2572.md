---
title: 編譯器錯誤 C2572
ms.date: 11/04/2016
f1_keywords:
- C2572
helpviewer_keywords:
- C2572
ms.assetid: f1a42d69-727d-4ce5-88c8-d5f55dea66ac
ms.openlocfilehash: 78402c054573de8c9860e96b6abe60ec5c3cfe38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395517"
---
# <a name="compiler-error-c2572"></a>編譯器錯誤 C2572

'class::member': 重複定義的預設參數： 參數的參數

無法重新定義預設參數。 如果您需要另一個值的參數，預設的參數應定義。

下列範例會產生 C2572:

```
// C2572.cpp
// compile with: /c
void f(int i = 1);   // function declaration

// function definition
void f(int i = 1) {}   // C2572

// try the following line instead
// void f(int i) {}
```