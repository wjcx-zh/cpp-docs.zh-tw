---
title: 編譯器錯誤 C2745
ms.date: 11/04/2016
f1_keywords:
- C2745
helpviewer_keywords:
- C2745
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
ms.openlocfilehash: 53a218fd80c6b8261aa0dda6bcaa1c347db73458
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563991"
---
# <a name="compiler-error-c2745"></a>編譯器錯誤 C2745

'token': 這個語彙基元無法轉換為識別項

識別碼必須是合法的字元所組成。

下列範例會產生 C2745:

```
// C2745.cpp
// compile with: /clr
int main() {
   int __identifier([));   // C2745
}
```