---
title: 編譯器錯誤 C2448
ms.date: 11/04/2016
f1_keywords:
- C2448
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
ms.openlocfilehash: 8a71fe05e2a046a65b659840f94d104a3c526778
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744156"
---
# <a name="compiler-error-c2448"></a>編譯器錯誤 C2448

' identifier '：函數樣式初始化運算式似乎是函式定義

函式定義不正確。

這個錯誤可能是因為舊式的 C 語言型式清單所造成。

下列範例會產生 C2448：

```cpp
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```
