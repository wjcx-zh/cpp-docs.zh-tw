---
title: 編譯器錯誤 C2645
ms.date: 11/04/2016
f1_keywords:
- C2645
helpviewer_keywords:
- C2645
ms.assetid: 6609c2fa-c3b2-4a6b-8e8d-58fb52f67175
ms.openlocfilehash: fa50cf4105c6ceb4f1104e0625ec6492e2d0461a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758225"
---
# <a name="compiler-error-c2645"></a>編譯器錯誤 C2645

成員的指標沒有限定名稱（找到 '：： * '）

成員指標的宣告未指定類別。

下列範例會產生 C2645：

```cpp
// C2645.cpp
class A {};
int main() {
   int B::* bp;   // C2645 B not defined
   int A::* ap;   // OK
}
```
