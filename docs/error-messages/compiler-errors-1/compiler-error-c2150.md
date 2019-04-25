---
title: 編譯器錯誤 C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: a9c6465ef87c12135ad4e6709741f0027d8ea3c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175143"
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