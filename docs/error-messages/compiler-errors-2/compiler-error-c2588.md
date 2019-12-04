---
title: 編譯器錯誤 C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: f1f73e2585606e7e86213607a96ef713345419c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755404"
---
# <a name="compiler-error-c2588"></a>編譯器錯誤 C2588

'：： ~ identifier '：不合法的全域析構函式

此析構函式是針對類別、結構或等位以外的專案所定義。 但這種作法並不合法。

此錯誤可能是因為範圍解析（`::`）運算子左邊的類別、結構或等位名稱遺失所造成。

下列範例會產生 C2588：

```cpp
// C2588.cpp
~F();   // C2588
```
