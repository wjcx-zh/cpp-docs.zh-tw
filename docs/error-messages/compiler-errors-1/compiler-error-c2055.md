---
title: 編譯器錯誤 C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 3c198168b4445e619148e5611621fa3ddba95d6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597271"
---
# <a name="compiler-error-c2055"></a>編譯器錯誤 C2055

預期的型式參數清單中，不是類型的清單

函式定義包含參數的型別清單，而不是型式參數清單。 ANSI C 要求的型式參數命名為，除非它們是 void 或省略符號 (`...`)。

下列範例會產生 C2055:

```
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```