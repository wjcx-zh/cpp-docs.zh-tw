---
title: 編譯器錯誤 C2802
ms.date: 11/04/2016
f1_keywords:
- C2802
helpviewer_keywords:
- C2802
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
ms.openlocfilehash: f872a4753907cd78c9118c22498777d5acc5b2fd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214577"
---
# <a name="compiler-error-c2802"></a>編譯器錯誤 C2802

靜態成員 ' operator operator ' 沒有型式參數

成員函式所宣告的運算子 **`static`** 必須至少有一個參數。

下列範例會產生 C2802：

```cpp
// C2802.cpp
// compile with: /clr /c
ref class A {
   static operator+ ();   // C2802
   static operator+ (A^, A^);   // OK
};
```
