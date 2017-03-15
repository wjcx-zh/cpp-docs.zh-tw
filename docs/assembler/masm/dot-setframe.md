---
title: ".SETFRAME | Microsoft Docs"
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
  - ".SETFRAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".SETFRAME directive"
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SETFRAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在框架的填滿註冊使用指定的暫存器的回溯資訊中的欄位和位移 \(`reg`\) 和偏移 \(`offset`\)。  位移必須是 16 的倍數，並且小於或等於 240。  這個指示詞也會產生`UWOP_SET_FPREG`回溯程式碼項目，如指定註冊使用目前的初構位移。  
  
## 語法  
  
```  
.SETFRAME reg, offset  
```  
  
## 備註  
 .SETFRAME 允許 ml64.exe 洏峈會指定如何框架函式回溯時，以及只允許在初構中，從延伸[PROC](../../assembler/masm/proc.md)框架宣告，以[.ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。  這些指示詞並不會產生程式碼路徑。 它們只會產生`.xdata`和`.pdata`。  .SETFRAME 前面必須有實際實作卸載動作的指示進行。  它是很好的作法，以包裝回溯指示詞，並將程式碼是在巨集中的回溯可確保合約。  
  
 如需詳細資訊，請參閱 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 範例  
  
### 描述  
 下列範例會示範如何使用框架指標:  
  
### 程式碼  
  
```  
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE  
_text SEGMENT  
frmex2 PROC FRAME  
   push rbp  
.pushreg rbp  
   sub rsp, 010h  
.allocstack 010h  
   mov rbp, rsp  
.setframe rbp, 0  
.endprolog  
   ; modify the stack pointer outside of the prologue (similar to alloca)  
   sub rsp, 060h  
  
   ; we can unwind from the following AV because of the frame pointer     
   mov rax, 0  
   mov rax, [rax] ; AV!  
  
   add rsp, 060h  
   add rsp, 010h  
   pop rbp  
   ret  
frmex2 ENDP  
_text ENDS  
END  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)