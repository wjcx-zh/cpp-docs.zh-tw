---
title: EVEN 和 ALIGN 指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- align
- EVEN
dev_langs:
- C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06a1007c50e3490e5b14e4da886494557be0d37e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688297"
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指示詞

**Microsoft 專屬**

雖然內嵌組合語言不支援大多數的 MASM 指示詞，但它確實支援`EVEN`並**對齊**。 這些指示詞放**NOP** （不執行作業） 所需的對齊標籤為特定界限的組譯碼中的指示。 這可讓某些處理器的指令擷取作業更有效率。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>