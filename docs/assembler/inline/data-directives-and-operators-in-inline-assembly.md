---
title: 資料指示詞和內嵌組譯碼中的運算子 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aff2f4c5ce5e7f5592aa9ec707d002c57f0eac0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678733"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>內嵌組譯碼中的資料指示詞和運算子

**Microsoft 專屬**

`__asm` 區塊可以參考 C 或 C++ 資料類型和物件，但無法定義含 MASM 指示詞或運算子的資料物件。 具體來說，您無法使用定義指示詞**DB**， `DW`， **DD**， `DQ`， `DT`，並`DF`，或運算子`DUP`或**這**。 也無法使用 MASM 結構和記錄。 內嵌組合語言不接受指示詞`STRUC`， `RECORD`，**寬度**，或**遮罩**。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>