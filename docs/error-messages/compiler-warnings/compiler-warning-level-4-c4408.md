---
title: 編譯器警告 （層級 4） C4408 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4408
dev_langs:
- C++
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7f804f8cbc3dce846783ce4937d7902d760511e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050186"
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