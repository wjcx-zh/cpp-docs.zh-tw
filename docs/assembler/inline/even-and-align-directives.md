---
title: EVEN 和 ALIGN 指示詞 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: a43425a4038ffb140eeaa0a9d111a39fc5c11ff0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指示詞
## <a name="microsoft-specific"></a>Microsoft 特定的  
 雖然內嵌組合語言不支援大多數的 MASM 指示詞，不過它支援`EVEN`和**對齊**。 這些指示詞放**NOP** （不執行作業） 的組件程式碼，視需要為特定界限的對齊標籤中的指示。 這可讓某些處理器的指令擷取作業更有效率。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)