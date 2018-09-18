---
title: 編譯器錯誤 C3198 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3198
dev_langs:
- C++
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb91d6f7b3ef6b8204a5f8bfb753db98ab6f93d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023380"
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