---
title: 編譯器錯誤 C2628
ms.date: 11/04/2016
f1_keywords:
- C2628
helpviewer_keywords:
- C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
ms.openlocfilehash: 4198d6ff0552f5280904ed1fea5e185df1a9c804
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754715"
---
# <a name="compiler-error-c2628"></a>編譯器錯誤 C2628

' type1 ' 後面接著 ' type2 ' 不合法（您是否忘記了 '; '？）

可能遺漏分號。

下列範例會產生 C2628：

```cpp
// C2628.cpp
class CMyClass {}
int main(){}   // C2628 error
```

可能的解決方案：

```cpp
// C2628b.cpp
class CMyClass {};
int main(){}
```
