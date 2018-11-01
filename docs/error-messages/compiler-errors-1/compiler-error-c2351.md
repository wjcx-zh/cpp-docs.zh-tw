---
title: 編譯器錯誤 C2351
ms.date: 11/04/2016
f1_keywords:
- C2351
helpviewer_keywords:
- C2351
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
ms.openlocfilehash: 2d93902ee0008a54da1b2ecf165e0a829362511f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665487"
---
# <a name="compiler-error-c2351"></a>編譯器錯誤 C2351

過時的 c + + 建構函式初始化語法

在新樣式的初始化清單建構函式中，必須明確地命名每個直接基底類別，即使它是唯一的基底類別。

下列範例會產生 C2351:

```
// C2351.cpp
// compile with: /c
class B {
public:
   B() : () {}   // C2351
   B() {}   // OK
};
```