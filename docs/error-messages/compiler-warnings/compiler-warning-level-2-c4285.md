---
title: 編譯器警告 (層級 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 96e1077ce3c9e60823a11aa41719738265ee703b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535976"
---
# <a name="compiler-warning-level-2-c4285"></a>編譯器警告 (層級 2) C4285

傳回型別為 'identifier:: operator->' 是遞迴套用使用中置標記法

指定**operator-> （)** 函式無法傳回的型別它被定義或為其定義之型別的參考。

下列範例會產生 C4285:

```
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```