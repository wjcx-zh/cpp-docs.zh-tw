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
ms.openlocfilehash: b6ac9f7174baf1e0ebe41181c6a6f43e7bb3f5d1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169093"
---
# <a name="using-operators-in-__asm-blocks"></a>在 __asm 區塊中使用運算子

**Microsoft 專屬**

`__asm` 區塊不能使用 C 或C++特定運算子，例如 **<<** 運算子。 不過，C 和 MASM 共用的運算子（例如 \* 運算子）會被視為組合語言運算子。 比方說，在 `__asm` 區塊外，方括弧（ **[]** ）會轉譯為封閉陣列注標，而 C 會自動調整為數組中專案的大小。 在 `__asm` 區塊內，方括號會視為 MASM 索引運算子，其會產生從任何資料物件或標籤 (不只是陣列) 的未縮放位元組位移。 下列程式碼將說明這項差異：

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

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
