---
title: 編譯器錯誤 C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: e060c2b9a38866a898a3c5ada9e595464050877e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756093"
---
# <a name="compiler-error-c2657"></a>編譯器錯誤 C2657

在語句開頭找到 ' class：:* ' （您是否忘了指定類型？）

行開頭為成員指標識別碼。

這個錯誤可能是因為成員指標的宣告中遺漏型別規範所造成。

下列範例會產生 C2657：

```cpp
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```
