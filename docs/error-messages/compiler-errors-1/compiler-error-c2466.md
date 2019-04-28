---
title: 編譯器錯誤 C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: 516f9b024947e0100a753e4e010a5b51b1fb24a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230525"
---
# <a name="compiler-error-c2466"></a>編譯器錯誤 C2466

無法配置常數大小為 0 的陣列

配置陣列，或宣告大小為零。 陣列大小的常數運算式必須是小於或等於零的整數。 為零的下標陣列宣告是合法的只針對類別、 結構或等位成員，並且只能使用 Microsoft 擴充功能 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

下列範例會產生 C2466:

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```