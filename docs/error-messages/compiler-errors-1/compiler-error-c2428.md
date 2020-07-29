---
title: 編譯器錯誤 C2428
ms.date: 11/04/2016
f1_keywords:
- C2428
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
ms.openlocfilehash: 2a85e1874a03882ca8497eeff379d377a585fe06
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216228"
---
# <a name="compiler-error-c2428"></a>編譯器錯誤 C2428

' operation '：不允許用在類型為 ' bool ' 的運算元上

您不能將遞減運算子套用至類型的物件 **`bool`** 。

下列範例會產生 C2428：

```cpp
// C2428.cpp
void g(bool fFlag) {
   --fFlag;   // C2428
   fFlag--;   // C2428
}
```
