---
title: 編譯器錯誤 C2428
ms.date: 11/04/2016
f1_keywords:
- C2428
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
ms.openlocfilehash: 9acaa3ba933f6fcf49a31e4973e7f6ddc3e178ea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744585"
---
# <a name="compiler-error-c2428"></a>編譯器錯誤 C2428

' operation '：不允許用在類型為 ' bool ' 的運算元上

您無法將遞減運算子套用至 `bool`類型的物件。

下列範例會產生 C2428：

```cpp
// C2428.cpp
void g(bool fFlag) {
   --fFlag;   // C2428
   fFlag--;   // C2428
}
```
