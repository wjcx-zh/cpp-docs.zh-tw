---
title: "內嵌組譯碼中的 MASM 巨集指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "指示詞, 巨集"
  - "內嵌組譯碼, 巨集指示詞"
  - "巨集, 指示詞"
  - "MASM (Microsoft Macro Assembler), 內嵌組譯碼巨集指示詞"
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 內嵌組譯碼中的 MASM 巨集指示詞
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 內嵌組合語言不是一種巨集組合語言。  您無法使用 MASM 巨集指示詞 \(**MACRO**、`REPT`、**IRC**、`IRP` 和 `ENDM`\) 或巨集運算子 \(**\<\>**、**\!**、**&**、`%` 和 `.TYPE`\)。  不過，`__asm` 區塊可以使用 C 前置處理器指示詞。  如需詳細資訊，請參閱[在 \_\_asm 區塊中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)