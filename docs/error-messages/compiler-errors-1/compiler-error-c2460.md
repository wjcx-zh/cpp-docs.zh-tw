---
title: 編譯器錯誤 C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: 414b6e53cf1610a55db984a1127bfc884102494f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230317"
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