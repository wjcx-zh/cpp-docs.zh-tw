---
title: 編譯器警告 (層級 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: e2e1781bf4c1b9ac0ee29d0b5900daa6cfe94b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199767"
---
# <a name="compiler-warning-level-1-c4269"></a>編譯器警告 (層級 1) C4269

' identifier '： ' const ' 自動使用編譯器所產生的預設值會產生不可靠的結果

非一般類別的**const**自動實例會使用編譯器產生的預設函式來初始化。

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

由於類別的這個實例是在堆疊上產生的，因此 `m_data` 的初始值可以是任何值。 此外，因為它是**常數**實例，所以永遠不會變更 `m_data` 的值。
