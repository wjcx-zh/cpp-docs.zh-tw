---
title: 編譯器警告（層級1） C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 84a0d4c541f67742d68c7f08e0dda52ccd350d04
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626703"
---
# <a name="compiler-warning-level-1-c4269"></a>編譯器警告（層級1） C4269

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