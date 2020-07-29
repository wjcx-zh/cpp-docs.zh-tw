---
title: 編譯器錯誤 C2166
ms.date: 11/04/2016
f1_keywords:
- C2166
helpviewer_keywords:
- C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
ms.openlocfilehash: a292a7d654861c265457ad26b009ae6f4b9cb54e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216332"
---
# <a name="compiler-error-c2166"></a>編譯器錯誤 C2166

左值 (l-value) 指定 const 物件

程式碼嘗試修改已宣告的專案 **`const`** 。

下列範例會產生 C2166：

```cpp
// C2166.cpp
int f();
int main() {
   ( (const int&) 1 ) = 5;   // C2166
}
```
