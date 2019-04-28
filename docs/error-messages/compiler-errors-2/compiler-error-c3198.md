---
title: 編譯器錯誤 C3198
ms.date: 11/04/2016
f1_keywords:
- C3198
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
ms.openlocfilehash: 61a3d14f9ad47edaa1e9b9f2b25d38b8dae7165c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243217"
---
# <a name="compiler-error-c3198"></a>編譯器錯誤 C3198

無效的浮點 pragma 使用方式： fenv_access pragma 只能在精確模式的運作

[fenv_access](../../preprocessor/fenv-access.md)下使用 pragma [/fp](../../build/reference/fp-specify-floating-point-behavior.md)以外的設定 **/fp： 精確**。

下列範例會產生 C3198:

```
// C3198.cpp
// compile with: /fp:fast
#pragma fenv_access(on)   // C3198
```