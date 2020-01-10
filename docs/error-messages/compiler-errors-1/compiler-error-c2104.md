---
title: 編譯器錯誤 C2104
ms.date: 11/04/2016
f1_keywords:
- C2104
helpviewer_keywords:
- C2104
ms.assetid: 2ea78896-72a6-4901-a1fa-f33ea88ad61b
ms.openlocfilehash: 2945f35379f29f2a163e654aae1f682a0914e40e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752219"
---
# <a name="compiler-error-c2104"></a>編譯器錯誤 C2104

已忽略位欄位上的 ' & '

您不能接受位欄位的位址。

下列範例會產生 C2104：

```cpp
// C2104.cpp
struct X {
   int sb : 1;
};

int main() {
   X x;
   &x.sb;   // C2104
   x.sb;   // OK
}
```
