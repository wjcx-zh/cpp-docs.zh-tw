---
title: 編譯器警告 (層級 4) C4408
ms.date: 11/04/2016
f1_keywords:
- C4408
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
ms.openlocfilehash: 3c7613d42bbd0ac7fa58a0b95ba68efb60d9f50a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391565"
---
# <a name="compiler-warning-level-4-c4408"></a>編譯器警告 (層級 4) C4408

anonymousstruct 或等位沒有宣告任何資料成員

匿名結構或等位必須至少有一個資料成員。

下列範例會產生 C4408：

```
// C4408.cpp
// compile with: /W4 /LD
static union
{
   // int i;
};
// a named union can have no data members
// } MyUnion;
```