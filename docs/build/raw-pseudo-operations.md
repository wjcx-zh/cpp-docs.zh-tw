---
title: "未經處理的虛擬作業 | Microsoft Docs"
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
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 未經處理的虛擬作業
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題列出各種虛擬作業及其概略說明。  
  
## 備註  
  
|虛擬作業|描述|  
|----------|--------|  
|PROC FRAME \[:ehandler\]|使 MASM 在 .pdata 中產生函式表項目並在 .xdata 中產生回溯資訊，供函式的結構化例外狀況處理 \(Structured Exception Handling\) 回溯行為使用。  如果提供 ehandler，則這個程序會輸入至 .xdata 做為語言特定處理常式。<br /><br /> 使用 FRAME 屬性時，之後必須跟隨 .ENDPROLOG 指示詞。  如果函式是分葉函式 \(如[函式類型](../build/function-types.md)所定義\)，則 FRAME 屬性為非必要，其餘的虛擬作業也是如此。|  
|.PUSHREG reg|使用目前初構的位移，產生指定編號的暫存器 UWOP\_PUSH\_NONVOL 回溯程式碼項目。<br /><br /> 這項作業應該只用於靜態整數暫存器。  對於動態暫存器的推入，請改用 .ALLOCSTACK 8。|  
|.SETFRAME reg, offset|使用指定的暫存器和位移，在回溯資訊中填入框架暫存器欄位和位移。  位移必須是 16 的倍數，並且小於或等於 240。  這個指示詞也使用目前的初構位移產生指定的暫存器之 UWOP\_SET\_FPREG 回溯程式碼進入點。|  
|.ALLOCSTACK size|使用指定的大小產生目前初構位移的 UWOP\_ALLOC\_SMALL 或 UWOP\_ALLOC\_LARGE。<br /><br /> size 運算元必須是 8 的倍數。|  
|.SAVEREG reg, offset|使用目前的初構位移，產生指定的暫存器和位移之 UWOP\_SAVE\_NONVOL 或 UWOP\_SAVE\_NONVOL\_FAR 回溯程式碼進入點。  MASM 會選擇最有效的編碼方式。<br /><br /> 位移必須為正數且為 8 的倍數。  位移為相對於程序框架的基底 \(通常是 RSP，如果使用框架指標，則為未調整的框架指標\)。|  
|.SAVEXMM128 reg, offset|使用目前的初構位移，產生指定的 XMM 暫存器和位移之 UWOP\_SAVE\_XMM128 或 UWOP\_SAVE\_XMM128\_FAR 回溯程式碼進入點。  MASM 會選擇最有效的編碼方式。<br /><br /> 位移必須為正數且為 16 的倍數。  位移為相對於程序框架的基底 \(通常是 RSP，如果使用框架指標，則為未調整的框架指標\)。|  
|.PUSHFRAME \[code\]|產生 UWOP\_PUSH\_MACHFRAME 回溯程式碼進入點。  如果指定選擇性的 code，則回溯程式碼進入點的修飾詞為 1，  否則修飾詞為 0。|  
|.ENDPROLOG|表示初構宣告的結束。  必須在函式的前 255 個位元組中使用。|  
  
 以下是函式初構範例，含有大多數 opcode 的適當用法：  
  
```  
sample PROC FRAME     
   db      048h; emit a REX prefix, to enable hot-patching  
push rbp  
.pushreg rbp  
sub rsp, 040h  
.allocstack 040h     
lea rbp, [rsp+020h]  
.setframe rbp, 020h  
movdqa [rbp], xmm7  
.savexmm128 xmm7, 020h;the offset is from the base of the frame  
;not the scaled offset of the frame  
mov [rbp+018h], rsi  
.savereg rsi, 038h  
mov [rsp+010h], rdi  
.savereg rdi, 010h; you can still use RSP as the base of the frame  
; or any other register you choose  
.endprolog  
  
; you can modify the stack pointer outside of the prologue (similar to alloca)  
; because we have a frame pointer.  
; if we didn’t have a frame pointer, this would be illegal  
; if we didn’t make this modification,  
; there would be no need for a frame pointer  
  
sub rsp, 060h  
  
; we can unwind from the following AV because of the frame pointer  
  
mov rax, 0  
mov rax, [rax] ; AV!  
  
; restore the registers that weren’t saved with a push  
; this isn’t part of the official epilog, as described in section 2.5  
  
movdqa xmm7, [rbp]  
mov rsi, [rbp+018h]  
mov rdi, [rbp-010h]  
  
; Here’s the official epilog  
  
lea rsp, [rbp-020h]  
pop rbp  
ret  
sample ENDP  
```  
  
## 請參閱  
 [MASM 的回溯 Helper](../build/unwind-helpers-for-masm.md)