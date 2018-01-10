---
title: "資料指示詞和運算子在內嵌組譯碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2352b1809f2c0377f17fde8127fcbda6464617a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>內嵌組譯碼中的資料指示詞和運算子
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `__asm` 區塊可以參考 C 或 C++ 資料類型和物件，但無法定義含 MASM 指示詞或運算子的資料物件。 具體來說，您不能使用定義指示詞**DB**， `DW`， **DD**， `DQ`， `DT`，和`DF`，或是運算子`DUP`或**這**。 也無法使用 MASM 結構和記錄。 內嵌組合語言不接受指示詞`STRUC`， `RECORD`，**寬度**，或**遮罩**。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)