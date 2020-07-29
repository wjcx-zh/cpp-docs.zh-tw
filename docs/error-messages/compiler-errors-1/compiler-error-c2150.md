---
title: 編譯器錯誤 C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: 419aa8229e0fe60d391345556c5fbd8be17558d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214733"
---
# <a name="compiler-error-c2150"></a>編譯器錯誤 C2150

> '*identifier*'：位欄位必須有類型 ' int '、' 帶正負號的 int ' 或 ' 不帶正負號的 int '

位欄位的基底類型必須是 **`int`** 、 **`signed int`** 或 **`unsigned int`** 。

## <a name="example"></a>範例

這個範例會顯示您可能會遇到 C2150 的情況，以及您可以如何修正此問題：

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```
