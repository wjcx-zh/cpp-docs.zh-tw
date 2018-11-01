---
title: 編譯器錯誤 C2570
ms.date: 11/04/2016
f1_keywords:
- C2570
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
ms.openlocfilehash: 447869b029df41219f71dcc633e9ae8a3934e0ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549574"
---
# <a name="compiler-error-c2570"></a>編譯器錯誤 C2570

'identifier': 等位不能有基底類別

等位是衍生自類別、 結構或等位。 這是不允許的。 改為將衍生的型別宣告為類別或結構。

下列範例會產生 C2570:

```
// C2570.cpp
// compile with: /c
class base {};
union hasPubBase : public base {};   // C2570
union hasNoBase {};   // OK
```