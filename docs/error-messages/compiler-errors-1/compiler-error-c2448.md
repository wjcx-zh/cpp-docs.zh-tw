---
title: 編譯器錯誤 C2448
ms.date: 11/04/2016
f1_keywords:
- C2448
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
ms.openlocfilehash: 915217ffbe848b2814e9960183854e09a80b9ee8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434849"
---
# <a name="compiler-error-c2448"></a>編譯器錯誤 C2448

'identifier': 函式樣式初始設定式似乎是函式定義

函式定義不正確。

此錯誤可能被因舊式 C 語言型式清單。

下列範例會產生 C2448:

```
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```