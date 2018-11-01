---
title: EVEN 和 ALIGN 指示詞
ms.date: 08/30/2018
f1_keywords:
- align
- EVEN
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 522d5689d680d0fc334743d2802abe21570dd6f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604346"
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指示詞

**Microsoft 專屬**

雖然內嵌組合語言不支援大多數的 MASM 指示詞，但它確實支援`EVEN`並**對齊**。 這些指示詞放**NOP** （不執行作業） 所需的對齊標籤為特定界限的組譯碼中的指示。 這可讓某些處理器的指令擷取作業更有效率。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>