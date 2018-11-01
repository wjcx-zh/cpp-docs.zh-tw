---
title: 編譯器錯誤 C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: 4e2816092b3c0c210ae2c544e9bf9a823a9c5d18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661132"
---
# <a name="compiler-error-c2657"></a>編譯器錯誤 C2657

' 類別:: *' 陳述式的開頭找到 （您是否忘記指定類型？）

行開頭的指標對成員識別項。

此錯誤可能被因成員指標的宣告中遺漏類型規範。

下列範例會產生 C2657:

```
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```