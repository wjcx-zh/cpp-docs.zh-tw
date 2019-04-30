---
title: 編譯器錯誤 C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 934e980149ad893e6799b0ab119a148fc5652fdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402784"
---
# <a name="compiler-error-c3199"></a>編譯器錯誤 C3199

無效的浮點 pragma 使用方式： 非精確模式不支援例外狀況

[Float_control](../../preprocessor/float-control.md) pragma 用來指定浮點例外狀況模型下的[/fp](../../build/reference/fp-specify-floating-point-behavior.md)以外的設定 **/fp： 精確**。

下列範例會產生 C3199:

```
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```