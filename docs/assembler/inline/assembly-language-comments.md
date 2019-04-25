---
title: 組合語言註解
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: fc37658eccd99b61d45aa9a9a7a2675ef90eee89
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167240"
---
# <a name="assembly-language-comments"></a>組合語言註解

**Microsoft 專屬**

`__asm` 區塊中的指令可使用組合語言註解：

```cpp
__asm mov ax, offset buff ; Load address of buff
```

由於 C 巨集會展開為單一邏輯資料行，請避免在巨集中使用組合語言註解。 (請參閱[__asm 區塊定義為 C 巨集](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。)`__asm`區塊可以包含 c-style 註解; 如需詳細資訊，請參閱 <<c2> [ 使用 C 或C++在 __asm 區塊中](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。</c2>

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>