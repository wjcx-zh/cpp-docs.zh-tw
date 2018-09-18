---
title: 編譯器錯誤 C2460 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2d85ffbc7aa799f0688fbb10021a04ef9455ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022607"
---
# <a name="compiler-error-c2460"></a>編譯器錯誤 C2460

'identifier1': 使用 'identifier2'，已經定義的

類別或結構 (`identifier2`) 宣告為成員本身 (`identifier1`)。 不允許遞迴定義的類別和結構。

下列範例會產生 C2460:

```
// C2460.cpp
class C {
   C aC;    // C2460
};
```

相反地，使用資料指標參考類別中。

```
// C2460.cpp
class C {
   C * aC;    // OK
};
```