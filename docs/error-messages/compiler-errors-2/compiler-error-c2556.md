---
title: 編譯器錯誤 C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 6b6f08ac52eff355f0857968817a681818e3c3dc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756769"
---
# <a name="compiler-error-c2556"></a>編譯器錯誤 C2556

' identifier '：多載函式只有傳回類型不同

多載函式具有不同的傳回型別，但具有相同的參數清單。 每個多載函數都必須有不同的型式參數清單。

下列範例會產生 C2556：

```cpp
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```
