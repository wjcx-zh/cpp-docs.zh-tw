---
title: EVEN 和 ALIGN 指示詞
ms.date: 08/30/2018
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: b191ce0942d7596090bfd7948a37a5c9e6aac15e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169431"
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指示詞

**Microsoft 專屬**

雖然內嵌組合語言不支援大多數的 MASM 指示詞，但它確實支援 `EVEN` 和**ALIGN**。 這些指示詞會視需要將**NOP** （無作業）指令放在元件程式碼中，以將標籤對齊特定界限。 這可讓某些處理器的指令擷取作業更有效率。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
