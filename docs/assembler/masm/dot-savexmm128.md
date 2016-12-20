---
title: ".SAVEXMM128 | Microsoft Docs"
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
  - ".SAVEXMM128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".SAVEXMM128 directive"
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAVEXMM128
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

其中一個會產生`UWOP_SAVE_XMM128`或`UWOP_SAVE_XMM128_FAR`回溯程式碼指定的 XMM 暫存器的輸入，並使用目前的初構位移的位移。  MASM 會選擇最有效的編碼方式。  
  
## 語法  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## 備註  
 .SAVEXMM128 允許 ml64.exe 洏峈會指定如何框架函式回溯時，以及只允許在初構中，從延伸[PROC](../../assembler/masm/proc.md)框架宣告，以[.ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。  這些指示詞並不會產生程式碼路徑。 它們只會產生`.xdata`和`.pdata`。  .SAVEXMM128 前面必須有實際實作卸載動作的指示進行。  它是很好的作法，以包裝回溯指示詞，並將程式碼是在巨集中的回溯可確保合約。  
  
 `offset`必須是 16 的倍數。  
  
 如需詳細資訊，請參閱 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)