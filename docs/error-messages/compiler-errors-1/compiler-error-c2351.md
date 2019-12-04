---
title: 編譯器錯誤 C2351
ms.date: 11/04/2016
f1_keywords:
- C2351
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
ms.openlocfilehash: 6839d0c44efa10ba9507389fea35964fa748d646
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759967"
---
# <a name="compiler-error-c2351"></a>編譯器錯誤 C2351

過時C++的函式初始化語法

在函式的新樣式初始化清單中，您必須明確命名每個直接基類，即使它是唯一的基類也一樣。

下列範例會產生 C2351：

```cpp
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```
