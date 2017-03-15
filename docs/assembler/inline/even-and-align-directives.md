---
title: "EVEN 和 ALIGN 指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "align"
  - "EVEN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALIGN 指示詞"
  - "指示詞, MASM"
  - "EVEN 指示詞"
  - "MASM (Microsoft Macro Assembler), 指示詞"
  - "NOP (無作業指令)"
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# EVEN 和 ALIGN 指示詞
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 雖然內嵌組合語言不支援大多數的 MASM 指示詞，不過它支援 `EVEN` 和 **ALIGN**。  這些指示詞會視需要將 **NOP** \(不執行作業\) 指令放置在組合語言程式碼中，做為特定界限的對齊標籤。  這可讓某些處理器的指令擷取作業更有效率。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)