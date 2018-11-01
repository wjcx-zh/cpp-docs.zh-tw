---
title: 編譯器錯誤 C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 4a2b4dc9dcd71d518845651dee97c566b778eb0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484141"
---
# <a name="compiler-error-c2556"></a>編譯器錯誤 C2556

'identifier': 多載函式只會因傳回型別

多載函式會有不同的傳回類型，而相同的參數清單。 每個多載函式必須有不同的型式參數清單。

下列範例會產生 C2556:

```
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```