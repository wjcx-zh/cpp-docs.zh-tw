---
title: 編譯器警告（層級2） C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 326b73dcf4665c442926e68995bace60300b6ebf
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052107"
---
# <a name="compiler-warning-level-2-c4285"></a>編譯器警告（層級2） C4285

如果使用中置標記法來套用 ' identifier：： operator-> ' 的傳回類型是遞迴的

指定的**operator-> （）** 函數無法傳回其定義的類型，或其定義所在之類型的參考。

下列範例會產生 C4285：

```cpp
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