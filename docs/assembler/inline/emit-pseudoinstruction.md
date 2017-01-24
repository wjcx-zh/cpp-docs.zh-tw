---
title: "_emit 虛擬指令 | Microsoft Docs"
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
  - "_emit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_emit 虛擬指令"
  - "位元組定義 (內嵌組譯碼)"
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _emit 虛擬指令
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 **\_emit** 虛擬指令會定義一個位元組，位於目前文字區段的目前位置。  **\_emit** 虛擬指令類似 MASM 的 [DB](../../assembler/masm/db.md) 指示詞。  
  
 下列片段將位元組 0x4A、0x43 和 0x4B 放入程式碼：  
  
```  
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B  
 .  
 .  
 .  
__asm {  
     randasm  
     }  
```  
  
> [!CAUTION]
>  如果 `_emit` 會產生修改暫存器的指令，而您以最佳化編譯應用程式，則編譯器無法判斷哪些暫存器會受到影響。  例如，如果 `_emit` 會產生修改 **rax** 暫存器的指令，編譯器不會知道 **rax** 已變更。  在內嵌組合語言程式碼執行之後，編譯器可能會對暫存器中的值做出不正確的假設。  因此，應用程式在執行時可能會表現出無法預期的行為。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)