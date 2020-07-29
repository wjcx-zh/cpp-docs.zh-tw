---
title: 編譯器警告 (層級 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: d0179dc5f5cb9367ee83a7f40f8b9ceb368474fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218126"
---
# <a name="compiler-warning-level-2-c4307"></a>編譯器警告 (層級 2) C4307

' operator '：整數常數溢位

運算子可用於導致整數常數的運算式溢出配置給它的空間。 您可能需要針對常數使用較大的類型。 會 **`signed int`** 保留比更小的值， **`unsigned int`** 因為會 **`signed int`** 使用一個位來表示正負號。

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
