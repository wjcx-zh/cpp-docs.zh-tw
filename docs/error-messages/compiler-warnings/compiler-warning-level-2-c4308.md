---
title: 編譯器警告（層級2） C4308
ms.date: 11/04/2016
f1_keywords:
- C4308
helpviewer_keywords:
- C4308
ms.assetid: d4e5c53c-71b2-4bbc-8a7c-3a2a3180d9d9
ms.openlocfilehash: 43bdfa1181ff45d80236ef1f07279eea67ebce0a
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052071"
---
# <a name="compiler-warning-level-2-c4308"></a>編譯器警告（層級2） C4308

負整數常數轉換成不帶正負號的類型

運算式會將負整數常數轉換成不帶正負號的類型。 運算式的結果可能沒有意義。

## <a name="example"></a>範例

```cpp
// C4308.cpp
// compile with: /W2
unsigned int u = (-5 + 3U);   // C4308

int main()
{
}
```