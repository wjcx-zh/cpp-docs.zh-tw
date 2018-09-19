---
title: 編譯器錯誤 C2150 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef0920c98fe59fe5bca49bba4c62a486a61c0a55
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024706"
---
# <a name="compiler-error-c2150"></a>編譯器錯誤 C2150

> '*識別碼*': 位元欄位必須有類型 'int'、 'signed 的 int' unsigned 的 int'

位元欄位的基礎類型必須是`int`， `signed int`，或`unsigned int`。

## <a name="example"></a>範例

這個範例示範如何可能會遇到 C2150，以及您如何修正它：

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```