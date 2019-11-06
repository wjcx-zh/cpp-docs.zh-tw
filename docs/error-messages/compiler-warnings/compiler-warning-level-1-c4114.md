---
title: 編譯器警告（層級1） C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 5662dba4339765db27d225eff2ad382ed56396ac
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626288"
---
# <a name="compiler-warning-level-1-c4114"></a>編譯器警告（層級1） C4114

相同類型的限定詞已經使用多次

類型宣告或定義使用類型限定詞（**const**、 **volatile**、**已簽署**或不**帶正負**號）一次以上。 這會導致含有 Microsoft extensions （/Ze）的警告，以及 ANSI 相容性（/Za）下的錯誤。

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
