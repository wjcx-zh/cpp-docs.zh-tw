---
title: 編譯器錯誤 C2496 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2496
dev_langs:
- C++
helpviewer_keywords:
- C2496
ms.assetid: 9a25237d-5bbb-4112-98f3-29cd99d3f89f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04e9e9a58c3ad64010aaffda2378f5b79cccbb67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062900"
---
# <a name="compiler-error-c2496"></a>編譯器錯誤 C2496

'identifier': 'selectany' 只能套用至具有外部連結的資料項目

[Selectany](../../cpp/selectany.md)屬性可以套用到外部可見和全域資料的項目。

下列範例會產生 C2496:

```
// C2496.cpp
// compile with: /c
__declspec(selectany) int x1 = 1;
const __declspec(selectany) int x2 = 2;   // C2496
static __declspec(selectany) int x6 = 6;   // C2496

extern const __declspec(selectany) int x3 = 3;

__declspec(selectany) int x4;

// dynamic initialization of x5
int f();
__declspec(selectany) int x5 = f();

extern const int x7;
// OK - redeclaration of x7 that is extern
const __declspec(selectany) int x7 = 7;
```