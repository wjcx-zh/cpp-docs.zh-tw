---
title: 編譯器錯誤 C2070 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2070
dev_langs:
- C++
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23daf8a8c25e132aa0717715a742352537010c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044076"
---
# <a name="compiler-error-c2070"></a>編譯器錯誤 C2070

'type': 不合法的 sizeof 運算元

[Sizeof](../../cpp/sizeof-operator.md)運算子需要運算式或類型名稱。

下列範例會產生 C2070:

```
// C2070.cpp
void func() {}
int main() {
   int a;
   a = sizeof(func);   // C2070
}
```

可能的解決方式：

```
// C2070b.cpp
void func() {}
int main() {
   int a;
   a = sizeof(a);
}
```