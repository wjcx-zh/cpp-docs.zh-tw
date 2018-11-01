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
ms.openlocfilehash: a871c19942252bf6a1a4901f8854b7b759700cd9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432795"
---
# <a name="using-operators-in-asm-blocks"></a>在 __asm 區塊中使用運算子

**Microsoft 專屬**

`__asm`區塊無法使用 C 或 c + + 專有的運算子，例如**<<** 運算子。 不過，共用的運算子 C 和 MASM，例如\*運算子，會解譯為組合語言運算子。 比方說外,`__asm`封鎖，方括號 (**[]**) 會解譯為封閉陣列註標，C 會自動調整大小的陣列中的項目。 在 `__asm` 區塊內，方括號會視為 MASM 索引運算子，其會產生從任何資料物件或標籤 (不只是陣列) 的未縮放位元組位移。 下列程式碼將說明這項差異：

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

`array` 的第一個參考不會加以縮放，但是第二個會加以縮放。 請注意，您可以使用**型別**進行縮放的運算子依據常數。 例如，以下為相等的陳述式：

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>