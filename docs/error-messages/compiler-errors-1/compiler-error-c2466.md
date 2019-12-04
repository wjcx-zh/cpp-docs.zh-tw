---
title: 編譯器錯誤 C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: aba4de518b9296fadc4746540e4e738c74908617
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743818"
---
# <a name="compiler-error-c2466"></a>編譯器錯誤 C2466

無法配置常數大小為0的陣列

已配置或宣告陣列，其大小為零。 陣列大小的常數運算式必須是大於零的整數。 具有零注標的陣列宣告僅適用于類別、結構或等位成員，且僅限於 Microsoft extensions （[/ze](../../build/reference/za-ze-disable-language-extensions.md)）。

下列範例會產生 C2466：

```cpp
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
