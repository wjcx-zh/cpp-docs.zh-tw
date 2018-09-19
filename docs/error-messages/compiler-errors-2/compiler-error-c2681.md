---
title: 編譯器錯誤 C2681 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2681
dev_langs:
- C++
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a0f0ab4b9c6a2dd2ae69f0370f808e32e496b97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059078"
---
# <a name="compiler-error-c2681"></a>編譯器錯誤 C2681

'type': 無效的運算式型別名稱

轉型運算子會嘗試將無效的型別轉換。 例如，如果您使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子，將運算式轉換成指標類型，來源運算式必須是指標。

下列範例會產生 C2681:

```
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```