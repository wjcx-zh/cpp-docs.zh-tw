---
title: 編譯器警告 （層級 1） C4584 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9db97bf35034f7ca628f860924bfb9a1fccc942f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036250"
---
# <a name="compiler-warning-level-1-c4584"></a>編譯器警告 (層級 1) C4584

'class1': 基底類別 'class2' 已經是 'class3 移' 基底類別

您所定義的類別繼承自一個繼承自另兩個類別。 例如: 

```
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

在此情況下，會發出警告在類別 C 因為它同時繼承自類別 A 和 B，也會繼承自類別 a 類別這個警告會作為提醒您必須完整限定使用自這些基底類別的成員，或將會產生編譯器錯誤，因為您對於哪些類別成員參考模稜兩可。