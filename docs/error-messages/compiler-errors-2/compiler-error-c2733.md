---
title: 編譯器錯誤 C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 3ef669a49f4a3ec5a1af1a15a79f2511fa2699dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755781"
---
# <a name="compiler-error-c2733"></a>編譯器錯誤 C2733

不允許多載函式 ' function ' 的第二個 C 連結

使用 C 連結宣告了一個以上的多載函式。 使用 C 連結時，只有一個指定函式的形式可以是外部。 因為多載函式具有相同的未裝飾名稱稱，所以無法搭配 C 程式使用。

下列範例會產生 C2733：

```cpp
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```
