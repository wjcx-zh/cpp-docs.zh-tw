---
title: 編譯器警告（層級2） C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: b5566bca22c328328a49e82268b96e8ec0fedc95
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052059"
---
# <a name="compiler-warning-level-2-c4307"></a>編譯器警告（層級2） C4307

' operator '：整數常數溢位

運算子可用於導致整數常數的運算式溢出配置給它的空間。 您可能需要針對常數使用較大的類型。 帶正負號的**int**會保留比 `unsigned int` 小的值，因為**帶正負**號的 int 會使用一個位來表示符號。

下列範例會產生 C4307：

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```