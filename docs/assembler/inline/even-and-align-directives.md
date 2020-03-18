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
ms.openlocfilehash: 63fa73988b9b9433a988035789a923ac73936214
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441587"
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指示詞

**Microsoft 專屬**

雖然內嵌組合語言不支援大多數的 MASM 指示詞，但它確實支援 `EVEN` 和**ALIGN**。 這些指示詞會視需要將**NOP** （無作業）指令放在元件程式碼中，以將標籤對齊特定界限。 這可讓某些處理器的指令擷取作業更有效率。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>