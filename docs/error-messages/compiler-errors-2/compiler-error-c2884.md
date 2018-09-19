---
title: 編譯器錯誤 C2884 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2884
dev_langs:
- C++
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d9266162d4608e39982cce1e94751e427bc5e47
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054710"
---
# <a name="compiler-error-c2884"></a>編譯器錯誤 C2884

'name': 由 using 宣告衝突與區域函式 'function'

您嘗試一次以上定義的函式。 第一個定義是本機的定義。 第二個是來自命名空間的`using`宣告。

下列範例會產生 C2884:

```
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```