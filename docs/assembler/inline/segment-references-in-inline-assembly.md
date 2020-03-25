---
title: 內嵌組譯碼中的區段參考
ms.date: 08/30/2018
helpviewer_keywords:
- references, inline assembly
- segment references in inline assembly
- inline assembly, segment references
- registers
- inline assembly, registers
- registers, inline assembly
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
ms.openlocfilehash: 865fc5fac5f46cdc8c55966e9989227d1d671d6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169249"
---
# <a name="segment-references-in-inline-assembly"></a>內嵌組譯碼中的區段參考

**Microsoft 專屬**

您必須依暫存器參考區段而不是依名稱 (例如區段名稱 `_TEXT` 無效)。 區段覆寫必須明確使用暫存器，如 ES:[BX]。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
