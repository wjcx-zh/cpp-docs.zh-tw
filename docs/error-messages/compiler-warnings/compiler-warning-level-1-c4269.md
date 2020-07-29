---
title: 編譯器警告 (層級 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 1b63d1af49a53b7b15cdbae912d79a1b4f0cf787
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230710"
---
# <a name="compiler-warning-level-1-c4269"></a>編譯器警告 (層級 1) C4269

' identifier '： ' const ' 自動使用編譯器所產生的預設值會產生不可靠的結果

**`const`** 非一般類別的自動實例會使用編譯器產生的預設函式來初始化。

## <a name="example"></a>範例

```cpp
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

因為這個類別的實例是在堆疊上產生的，所以的初始值 `m_data` 可以是任何專案。 此外，由於它是 **`const`** 實例，因此 `m_data` 永遠不會變更的值。
