---
title: 編譯器警告（層級1） C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 8d2b0339ff3cce9a68dce57a5f2b4efac076c5c2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233310"
---
# <a name="compiler-warning-level-1-c4114"></a>編譯器警告（層級1） C4114

相同類型的限定詞已經使用多次

類型宣告或定義使用類型限定詞（ **`const`** 、 **`volatile`** 、 **`signed`** 或 **`unsigned`** ）多次。 這會導致含有 Microsoft extensions （/Ze）的警告，以及 ANSI 相容性（/Za）下的錯誤。

下列範例會產生 C4114：

```cpp
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

下列範例會產生 C4114：

```cpp
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
