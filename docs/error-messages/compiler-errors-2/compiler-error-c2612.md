---
title: 編譯器錯誤 C2612
ms.date: 11/04/2016
f1_keywords:
- C2612
helpviewer_keywords:
- C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
ms.openlocfilehash: 630e5b1cc6e99ffda28f50c09bccbbc2fea07172
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737695"
---
# <a name="compiler-error-c2612"></a>編譯器錯誤 C2612

尾端 ' char ' 在基底/成員初始化運算式清單中不合法

字元會出現在初始化運算式清單中的最後一個基底或成員之後。

下列範例會產生 C2612：

```cpp
// C2612.cpp
class A {
public:
   int i;
   A( int ia ) : i( ia ) + {};   // C2612
};
```
