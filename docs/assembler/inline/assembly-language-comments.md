---
title: 組合語言註解 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02f4c493bac5c2a066dc0b24e2a566d49345288d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683322"
---
# <a name="assembly-language-comments"></a>組合語言註解

**Microsoft 專屬**

`__asm` 區塊中的指令可使用組合語言註解：

```cpp
__asm mov ax, offset buff ; Load address of buff
```

由於 C 巨集會展開為單一邏輯資料行，請避免在巨集中使用組合語言註解。 (請參閱[__asm 區塊定義為 C 巨集](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。)`__asm`區塊可以包含 c-style 註解; 如需詳細資訊，請參閱 <<c2> [ 使用 C 或 c + + 在 __asm 區塊中的](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>