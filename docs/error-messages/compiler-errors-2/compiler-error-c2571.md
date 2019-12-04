---
title: 編譯器錯誤 C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: 7bd87f0732e1a632b8c86cc57fab1a0f104b2c77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755495"
---
# <a name="compiler-error-c2571"></a>編譯器錯誤 C2571

' function '：虛擬函式不能在聯集 ' union ' 中

Union 是以虛擬函數宣告。 您只能在類別或結構中宣告虛擬函式。  可能的解決方式：

1. 將聯集變更為類別或結構。

1. 將函式設為非虛擬。

下列範例會產生 C2571：

```cpp
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```
