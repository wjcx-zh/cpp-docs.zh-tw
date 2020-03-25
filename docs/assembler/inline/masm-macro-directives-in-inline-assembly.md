---
title: 內嵌組譯碼中的 MASM 巨集指示詞
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 38b73346fc52f6b5efe478f8eb960ad049fae924
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169275"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>內嵌組譯碼中的 MASM 巨集指示詞

**Microsoft 專屬**

內嵌組合語言不是一種巨集組合語言。 您無法使用 MASM 宏指示詞（**宏**、`REPT`、 **IRC**、`IRP`和 `ENDM`）或宏運算子（ **<>** 、 **！** 、 **&** 、`%`和 `.TYPE`）。 不過，`__asm` 區塊可以使用 C 前置處理器指示詞。 如需詳細資訊，請參閱[在 __Asm 區塊中使用 C 或C++ ](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) 。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
