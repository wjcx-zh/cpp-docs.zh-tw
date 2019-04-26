---
title: 內嵌組譯碼中的 MASM 巨集指示詞
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 7e1bed782d28a5bf7c934c3f57f50aae70038578
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167253"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>內嵌組譯碼中的 MASM 巨集指示詞

**Microsoft 專屬**

內嵌組合語言不是一種巨集組合語言。 您無法使用 MASM 巨集指示詞 (**巨集**， `REPT`， **IRC**， `IRP`，以及`ENDM`) 或巨集運算子 (**<>**，**!**， **&**， `%`，和`.TYPE`)。 不過，`__asm` 區塊可以使用 C 前置處理器指示詞。 請參閱[使用 C 或C++在 __asm 區塊中](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)如需詳細資訊。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>