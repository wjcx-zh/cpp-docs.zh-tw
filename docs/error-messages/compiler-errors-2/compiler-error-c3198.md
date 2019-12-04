---
title: 編譯器錯誤 C3198
ms.date: 11/04/2016
f1_keywords:
- C3198
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
ms.openlocfilehash: b9e0ce4a84b312e3a9277898b3fc264ea3ae22bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739151"
---
# <a name="compiler-error-c3198"></a>編譯器錯誤 C3198

使用浮點 pragma 無效： fenv_access pragma 只能以精確模式運作

在 **/fp：精確**的[/fp](../../build/reference/fp-specify-floating-point-behavior.md)設定底下使用了[fenv_access](../../preprocessor/fenv-access.md) pragma。

下列範例會產生 C3198：

```cpp
// C3198.cpp
// compile with: /fp:fast
#pragma fenv_access(on)   // C3198
```
