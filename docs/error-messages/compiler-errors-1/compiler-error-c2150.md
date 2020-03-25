---
title: 編譯器錯誤 C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: 57c21f7ee9435220a9ca0b50bb85567506b6ad3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207216"
---
# <a name="compiler-error-c2150"></a>編譯器錯誤 C2150

> '*identifier*'：位欄位必須有類型 ' int '、' 帶正負號的 int ' 或 ' 不帶正負號的 int '

需要 `int`、`signed int`或 `unsigned int`的位欄位基底類型。

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
