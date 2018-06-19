---
title: .SETFRAME |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SETFRAME
dev_langs:
- C++
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c49d512534a11f01376deac41006e55c6b7b9d89
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052582"
---
# <a name="setframe"></a>.SETFRAME
框架填滿註冊中使用指定的暫存器的回溯資訊的欄位和位移 (`reg`) 和位移 (`offset`)。 位移必須是 16 的倍數，且小於或等於 240。 這個指示詞也會產生`UWOP_SET_FPREG`指定登錄使用的目前位移，序言回溯程式碼項目。  
  
## <a name="syntax"></a>語法  
  
```  
.SETFRAME reg, offset  
```  
  
## <a name="remarks"></a>備註  
 .SETFRAME 允許 ml64.exe 使用者指定框架的函式的回溯時，如何，而且只允許序言，會從延伸內[PROC](../../assembler/masm/proc.md)框架宣告[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼。它們只會產生`.xdata`和`.pdata`。 .SETFRAME 之前應該加實際實作卸載動作的指示。 它是最好的作法是包裝回溯指示詞，以確保協議為了在巨集中的回溯程式碼。  
  
 如需詳細資訊，請參閱[MASM (ml64.exe) x64](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="sample"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會示範如何使用框架指標：  
  
### <a name="code"></a>程式碼  
  
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
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)