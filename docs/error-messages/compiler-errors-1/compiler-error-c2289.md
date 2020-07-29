---
title: 編譯器錯誤 C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 239552eb383197e57fcc6285cbf416c7c71c858b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216267"
---
# <a name="compiler-error-c2289"></a>編譯器錯誤 C2289

相同類型的限定詞已經使用多次

類型宣告或定義使用類型限定詞（ **`const`** 、 **`volatile`** 、 **`signed`** 或 **`unsigned`** ）多次，導致 ANSI 相容性（**/za**）發生錯誤。

下列範例會產生 C2286：

```cpp
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```
