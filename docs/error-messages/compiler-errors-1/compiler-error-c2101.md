---
title: 編譯器錯誤 C2101
ms.date: 11/04/2016
f1_keywords:
- C2101
helpviewer_keywords:
- C2101
ms.assetid: 42f0136f-8cc1-4f2b-be1c-721ec9278e66
ms.openlocfilehash: 8bea258bd3e20cba1dbfabdd3a669a44414b89f8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752336"
---
# <a name="compiler-error-c2101"></a>編譯器錯誤 C2101

不可在常數上使用 '&'

傳址運算子 ( `&` ) 必須將左值 (l-value) 作為運算元。

下列範例會產生 C2101：

```cpp
// C2101.cpp
int main() {
   char test;
   test = &'a';   // C2101
   test = 'a';   // OK
}
```
