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
ms.openlocfilehash: bcacb0cdd26181da3cf80a582866c1e30567d043
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192349"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>內嵌組譯碼中的資料指示詞和運算子

**Microsoft 特定的**

雖然 **`__asm`** 區塊可以參考 C 或 c + + 資料類型和物件，但它無法定義具有 MASM 指示詞或運算子的資料物件。 具體而言，您不能使用定義指示詞**DB**、 `DW` 、 **DD**、、 `DQ` `DT` 和 `DF` ，或是運算子 `DUP` 或**這個**。 也無法使用 MASM 結構和記錄。 內嵌組合語言不接受指示詞 `STRUC` 、 `RECORD` 、 **WIDTH**或**MASK**。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用元件語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
