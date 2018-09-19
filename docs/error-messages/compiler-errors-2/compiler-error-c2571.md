---
title: 編譯器錯誤 C2571 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30cc078251d0511da77e08690db275a788973ffb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067931"
---
# <a name="compiler-error-c2571"></a>編譯器錯誤 C2571

'function': 虛擬函式不能在等位 'union'

等位宣告具有虛擬函式。 您可以宣告只能在類別或結構中的虛擬函式。  可能的解決方式：

1. 將類別或結構的聯集。

1. 讓非虛擬函式。

下列範例會產生 C2571:

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```