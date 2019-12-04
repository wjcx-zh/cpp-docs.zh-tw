---
title: 編譯器錯誤 C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: a7d20a7658a75a492e19b9e81acaa3b6fce5cae7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743935"
---
# <a name="compiler-error-c2460"></a>編譯器錯誤 C2460

' identifier1 '：使用正在定義的 ' identifier2 '

類別或結構（`identifier2`）會宣告為本身的成員（`identifier1`）。 不允許遞迴定義類別和結構。

下列範例會產生 C2460：

```cpp
// C2460.cpp
class C {
   C aC;    // C2460
};
```

相反地，請使用類別中的指標參考。

```cpp
// C2460.cpp
class C {
   C * aC;    // OK
};
```
