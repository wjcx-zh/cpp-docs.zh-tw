---
title: 編譯器錯誤 C2698 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7ca3e7568640aabd2b7960d97ea94a11a1d5d59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118917"
---
# <a name="compiler-error-c2698"></a>編譯器錯誤 C2698

using 宣告為 'declaration 1' 不能同時存在與 using 宣告為' declaration 2'

一旦[using 宣告](../../cpp/using-declaration.md)資料成員，任何使用不允許使用相同的名稱與相同範圍中的宣告，因為只有函式可以多載。

下列範例會產生 C2698:

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```