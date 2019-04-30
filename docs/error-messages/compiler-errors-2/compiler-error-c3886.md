---
title: 編譯器錯誤 C3886
ms.date: 11/04/2016
f1_keywords:
- C3886
helpviewer_keywords:
- C3886
ms.assetid: 485f6c12-cc1b-4146-9034-409a0a5e615e
ms.openlocfilehash: e9e9d4b478d5b53e50203d1f009295e1da444f2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402537"
---
# <a name="compiler-error-c3886"></a>編譯器錯誤 C3886

'var': 必須初始化常值資料成員

A[常值](../../extensions/literal-cpp-component-extensions.md)時加以初始化，必須先初始化變數。

下列範例會產生 C3886:

```
// C3886.cpp
// compile with: /clr /c
ref struct Y1 {
   literal int staticConst;   // C3886
   literal int staticConst2 = 0;   // OK
};
```