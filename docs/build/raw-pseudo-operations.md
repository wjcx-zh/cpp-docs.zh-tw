---
title: "未經處理的虛擬作業 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52ce7fb4455f87001bcfe87e1368ed0c09cda6b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="raw-pseudo-operations"></a>未經處理的虛擬作業
本主題列出的虛擬作業。  
  
## <a name="remarks"></a>備註  
  
|虛擬操作|描述|  
|----------------------|-----------------|  
|PROC 框架 [: ehandler]|原因要產生的函式的 MASM 表格項目中的.pdata 和回溯.xdata 中的資訊的函式的結構化例外狀況處理回溯行為。  如果 ehandler 存在時，此程序中輸入的.xdata 為語言特定處理常式。<br /><br /> 使用框架屬性時，它必須後面。ENDPROLOG 指示詞。  如果函式的分葉函式 (如中所定義[函式型別](../build/function-types.md)) 框架屬性是不必要的因為這些虛擬作業的其餘部分。|  
|.PUSHREG reg|產生使用目前在序言中位移的指定暫存器號碼 UWOP_PUSH_NONVOL 回溯程式碼項目。<br /><br /> 這應該只用於靜態整數暫存器。  動態暫存器的推播通知，針對使用。ALLOCSTACK 8，改為|  
|.SETFRAME reg 位移|框架填滿註冊中使用指定的暫存器和位移的回溯資訊的欄位和位移。 位移必須是 16 的倍數，且小於或等於 240。 這個指示詞也會產生指定的暫存器使用的目前序言位移 UWOP_SET_FPREG 回溯程式碼項目。|  
|.ALLOCSTACK 大小|在序言中，會產生 UWOP_ALLOC_SMALL 或 UWOP_ALLOC_LARGE 具有指定大小的目前位移。<br /><br /> 大小運算元必須是 8 的倍數。|  
|.SAVEREG reg 位移|產生 UWOP_SAVE_NONVOL 或指定的暫存器和位移使用目前的序言位移 UWOP_SAVE_NONVOL_FAR 回溯程式碼項目。 MASM 會選擇最有效率的編碼方式。<br /><br /> 位移必須是正數且 8 的倍數。  位移會與基底的程序的範圍內，通常是 RSP，或者，如果使用框架指標，無縮放的框架指標。|  
|.SAVEXMM128 reg 位移|產生 UWOP_SAVE_XMM128 或指定 xmm 暫存器和位移使用目前的序言位移 UWOP_SAVE_XMM128_FAR 回溯程式碼項目。 MASM 會選擇最有效率的編碼方式。<br /><br /> 位移必須是正數且 16 的倍數。  位移會與基底的程序的範圍內，通常是 RSP，或者，如果使用框架指標，無縮放的框架指標。|  
|.PUSHFRAME [程式碼]|產生 UWOP_PUSH_MACHFRAME 回溯程式碼項目。 如果指定選擇性的程式碼，則回溯程式碼項目指定為 1 的修飾詞。 否則修飾詞是 0。|  
|.ENDPROLOG|表示序言宣告的結尾。  必須存在於函式的第一個 255 個位元組。|  
  
 以下是範例函式初構與大部分的 opcode 的正確用法：  
  
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
  
## <a name="see-also"></a>請參閱  
 [MASM 的回溯協助程式](../build/unwind-helpers-for-masm.md)