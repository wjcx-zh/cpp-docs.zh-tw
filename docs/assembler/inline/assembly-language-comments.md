---
title: 組合語言註解
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: 2e993bd48c7ec801abd440676c80a5bd8f7b42ec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192726"
---
# <a name="assembly-language-comments"></a>組合語言註解

**Microsoft 特定的**

區塊中的指示 **`__asm`** 可以使用元件語言批註：

```cpp
__asm mov ax, offset buff ; Load address of buff
```

由於 C 巨集會展開為單一邏輯資料行，請避免在巨集中使用組合語言註解。 （請參閱將[__Asm 區塊定義為 C 宏](../../assembler/inline/defining-asm-blocks-as-c-macros.md)）。**`__asm`** 區塊也可以包含 C 樣式的批註。如需詳細資訊，請參閱[在 __asm 區塊中使用 c 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用元件語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
