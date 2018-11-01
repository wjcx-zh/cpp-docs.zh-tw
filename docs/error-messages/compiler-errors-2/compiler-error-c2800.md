---
title: 編譯器錯誤 C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: e893866a28c124e9e6cbc9663a488f89ac2d291b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516892"
---
# <a name="compiler-error-c2800"></a>編譯器錯誤 C2800

無法多載 'operator operator'

下列運算子無法多載： 類別成員存取 (`.`)，成員的指標 (`.*`)，範圍解析 (`::`)，條件運算式 (`? :`)，和`sizeof`。

下列範例會產生 C2800:

```
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```