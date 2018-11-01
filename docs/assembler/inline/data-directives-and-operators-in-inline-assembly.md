---
title: 內嵌組譯碼中的資料指示詞和運算子
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: 52e20c37f3066122a062e3fc9c64ced576b6c302
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577968"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>內嵌組譯碼中的資料指示詞和運算子

**Microsoft 專屬**

`__asm` 區塊可以參考 C 或 C++ 資料類型和物件，但無法定義含 MASM 指示詞或運算子的資料物件。 具體來說，您無法使用定義指示詞**DB**， `DW`， **DD**， `DQ`， `DT`，並`DF`，或運算子`DUP`或**這**。 也無法使用 MASM 結構和記錄。 內嵌組合語言不接受指示詞`STRUC`， `RECORD`，**寬度**，或**遮罩**。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>