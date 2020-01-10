---
title: 編譯器錯誤 C2947
ms.date: 11/04/2016
f1_keywords:
- C2947
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
ms.openlocfilehash: 7056c13edca534701ffe82f0169897ea804f40d7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755352"
---
# <a name="compiler-error-c2947"></a>編譯器錯誤 C2947

必須是 ' > ' 才能終止結構，但找到 ' 語法 '

泛型或樣板引數清單可能未正確地終止。

C2947 也可以由語法錯誤產生。

下列範例會產生 C2947：

```cpp
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```
