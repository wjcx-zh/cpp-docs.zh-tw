---
title: 在 __asm 區塊中使用運算子
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: cdcfee20cfdc5a6dc315d00ef024d1616900a2e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191101"
---
# <a name="using-operators-in-__asm-blocks"></a>在 __asm 區塊中使用運算子

**Microsoft 特定的**

**`__asm`** 區塊不能使用 C 或 c + + 特定運算子，例如 **<<** 運算子。 不過，C 和 MASM 共用的運算子（例如 \* 運算子）會被視為組合語言運算子。 例如，在區塊外 **`__asm`** ，方括弧（**[]**）會解讀為封閉陣列注標，而 C 會自動調整為數組中專案的大小。 在 **`__asm`** 區塊內，它們會被視為 MASM 索引運算子，它會從任何資料物件或標籤（而不只是陣列）產生無比例的位元組位移。 下列程式碼將說明這項差異：

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

`array` 的第一個參考不會加以縮放，但是第二個會加以縮放。 請注意，您可以使用**類型**運算子，根據常數來達到調整。 例如，下列陳述式是相等的：

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用 C 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
