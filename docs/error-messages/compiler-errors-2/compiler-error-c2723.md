---
title: 編譯器錯誤 C2723 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2723
dev_langs:
- C++
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b1be2d81ecec7eb96fd9c1cd7e9938ce509f71e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072013"
---
# <a name="compiler-error-c2723"></a>編譯器錯誤 C2723

'function' : 函式定義上的 'specifier' 規範不合法

規範不能出現在類別宣告之外的函式定義。 只可以在類別宣告中的成員函式宣告上指定 `virtual` 規範。

下列範例會產生 C2723，並示範如何修正此問題：

```
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```