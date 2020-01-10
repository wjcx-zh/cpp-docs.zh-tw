---
title: 編譯器錯誤 C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 0dfe9f88fcdfda1325150d480670777a4d42d896
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758628"
---
# <a name="compiler-error-c2537"></a>編譯器錯誤 C2537

' 規範 '：不合法的連結規格

可能的原因:

1. 不支援連結規範。 僅支援 "C" 連結規範。

1. "C" 連結是針對一組多載函式中的一個以上函式所指定。 但這種作法並不合法。

下列範例會產生 C2537：

```cpp
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```
