---
title: 編譯器警告 (層級 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: e471ca3e478d1166b150e49bf25efa4b9d5803cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569269"
---
# <a name="compiler-warning-level-1-c4606"></a>編譯器警告 (層級 1) C4606

\#pragma 警告: 'warning_number' 忽略;程式碼分析警告未與警告層級相關聯

程式碼分析警告，只有`error`， `once`，並`default`支援[警告](../../preprocessor/warning.md)pragma。

## <a name="example"></a>範例

下列範例會產生 C4606。

```
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```