---
title: 編譯器錯誤 C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: 1f03b196b7ddaae80dac1941cdde5be16acace5f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748680"
---
# <a name="compiler-error-c2153"></a>編譯器錯誤 C2153

十六進位常數必須至少有一個十六進位數位

十六進位常數0x、0X 和 \x 無效。 至少要有一個十六進位數位必須遵循 x 或 X。

下列範例會產生 C2153：

```cpp
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```
