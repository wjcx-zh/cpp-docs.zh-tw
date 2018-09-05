---
title: 在內嵌組譯碼中的 MASM 巨集指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35ad22a9a4b79a31665ab6b156f8174d395bb0ee
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687969"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>內嵌組譯碼中的 MASM 巨集指示詞

**Microsoft 專屬**

內嵌組合語言不是一種巨集組合語言。 您無法使用 MASM 巨集指示詞 (**巨集**， `REPT`， **IRC**， `IRP`，以及`ENDM`) 或巨集運算子 (**<>**，**!**， **&**， `%`，和`.TYPE`)。 不過，`__asm` 區塊可以使用 C 前置處理器指示詞。 請參閱[使用 C 或 c + + 在 __asm 區塊中的](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)如需詳細資訊。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>