---
title: 編譯器錯誤 C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 2f0ca98dc44a78adde378a0f80078ae30c590e11
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738813"
---
# <a name="compiler-error-c3199"></a>編譯器錯誤 C3199

使用浮點 pragma 無效：非精確模式不支援例外狀況

[Float_control](../../preprocessor/float-control.md) pragma 是用來指定[/fp 設定底下的浮點](../../build/reference/fp-specify-floating-point-behavior.md)例外狀況模型，而不是 **/fp：精確**。

下列範例會產生 C3199：

```cpp
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```
