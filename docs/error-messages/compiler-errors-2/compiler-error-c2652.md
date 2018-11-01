---
title: 編譯器錯誤 C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: 9c9772052b690ad87de1d408c06478d82d48e724
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464801"
---
# <a name="compiler-error-c2652"></a>編譯器錯誤 C2652

'identifier': 不合法的複製建構函式： 第一個參數不得為 'identifier'

中的複製建構函式的第一個參數具有相同的類別、 結構或等位為其定義的型別。 第一個參數可以是參考型別，但不是類型本身。

下列範例會產生 C2651:

```
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```