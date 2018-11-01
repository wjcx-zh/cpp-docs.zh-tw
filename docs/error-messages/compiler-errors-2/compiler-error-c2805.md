---
title: 編譯器錯誤 C2805
ms.date: 11/04/2016
f1_keywords:
- C2805
helpviewer_keywords:
- C2805
ms.assetid: c997dc56-e199-442f-b94e-ac551ec9b015
ms.openlocfilehash: b0b3c0d4291787fb0b5664baa9159c84c8549dfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471730"
---
# <a name="compiler-error-c2805"></a>編譯器錯誤 C2805

二進位 '運算子 operator operator' 的參數太少

二元運算子沒有任何參數。

下列範例會產生 C2805:

```
// C2805.cpp
// compile with: /c
class X {
public:
   X operator< ( void );   // C2805 must take one parameter
   X operator< ( X );   // OK
};
```