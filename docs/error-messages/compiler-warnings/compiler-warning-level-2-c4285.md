---
title: 編譯器警告 (層級 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 96e1077ce3c9e60823a11aa41719738265ee703b
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345382"
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