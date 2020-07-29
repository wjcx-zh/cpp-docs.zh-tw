---
title: 內嵌組譯碼中的 MASM 巨集指示詞
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 964f70aeef6e0e62ac4b941b2cc26d3e7c7ef466
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191790"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>內嵌組譯碼中的 MASM 巨集指示詞

**Microsoft 特定的**

內嵌組合語言不是一種巨集組合語言。 您無法使用 MASM 宏指示詞（**宏**、 `REPT` 、 **IRC**、 `IRP` 和 `ENDM` ）或宏運算子（ **<>** 、 **！**、 **&** 、 `%` 和 `.TYPE` ）。 **`__asm`** 不過，區塊可以使用 C 預處理器指示詞。 如需詳細資訊，請參閱[在 __Asm 區塊中使用 C 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) 。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用元件語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
