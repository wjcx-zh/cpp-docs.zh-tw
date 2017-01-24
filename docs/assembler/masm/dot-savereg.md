---
title: ".SAVEREG | Microsoft Docs"
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
  - ".SAVEREG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".SAVEREG directive"
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAVEREG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

其中一個會產生`UWOP_SAVE_NONVOL`或`UWOP_SAVE_NONVOL_FAR`回溯程式碼指定的暫存器的輸入 \(`reg`\) 和偏移 \(`offset`\) 使用目前的初構位移。  MASM 會選擇最有效的編碼方式。  
  
## 語法  
  
```  
.SAVEREG reg, offset  
```  
  
## 備註  
 .SAVEREG 允許 ml64.exe 洏峈指定框架的函式的回溯，並只允許在初構中，從延伸[PROC](../../assembler/masm/proc.md)框架宣告，以[.ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。  這些指示詞並不會產生程式碼路徑。 它們只會產生`.xdata`和`.pdata`。  .SAVEREG 前面必須有實際實作卸載動作的指示進行。  它是很好的作法，以包裝回溯指示詞，並將程式碼是在巨集中的回溯可確保合約。  
  
 如需詳細資訊，請參閱 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)