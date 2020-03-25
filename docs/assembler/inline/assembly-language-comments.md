---
title: 組合語言註解
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: a8b2c98c61d58d72e78dbffd4f3b6ed7707d2d7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169600"
---
# <a name="assembly-language-comments"></a>組合語言註解

**Microsoft 專屬**

`__asm` 區塊中的指令可使用組合語言註解：

```cpp
__asm mov ax, offset buff ; Load address of buff
```

由於 C 巨集會展開為單一邏輯資料行，請避免在巨集中使用組合語言註解。 （請參閱將[__Asm 區塊定義為 C 宏](../../assembler/inline/defining-asm-blocks-as-c-macros.md)）。`__asm` 區塊也可以包含 C 樣式的批註;如需詳細資訊，請參閱[在C++ __Asm 區塊中使用 C 或](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
