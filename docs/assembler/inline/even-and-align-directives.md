---
title: "EVEN 和 ALIGN 指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- align
- EVEN
dev_langs: C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5048e9f8c2991133ad0cf28720b9236232cc9337
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指示詞
## <a name="microsoft-specific"></a>Microsoft 特定的  
 雖然內嵌組合語言不支援大多數的 MASM 指示詞，不過它支援`EVEN`和**對齊**。 這些指示詞放**NOP** （不執行作業） 的組件程式碼，視需要為特定界限的對齊標籤中的指示。 這可讓某些處理器的指令擷取作業更有效率。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)