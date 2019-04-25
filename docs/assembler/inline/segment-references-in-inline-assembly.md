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
ms.openlocfilehash: 5c07fa897da23a55f376a20e7588c8c8c269d1a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167370"
---
# <a name="segment-references-in-inline-assembly"></a>內嵌組譯碼中的區段參考

**Microsoft 專屬**

您必須依暫存器參考區段而不是依名稱 (例如區段名稱 `_TEXT` 無效)。 區段覆寫必須明確使用暫存器，如 ES:[BX]。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>