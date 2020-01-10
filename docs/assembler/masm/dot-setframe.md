---
title: .SETFRAME
ms.date: 12/17/2019
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: 8c491a811634995398a37aa001cc1c93f8434114
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318237"
---
# <a name="setframe"></a>.SETFRAME

使用指定的暫存器（*reg*）和位移（*位移*），填入 [框架暫存器] 欄位，以及回溯資訊中的位移。 位移必須是16的倍數，且小於或等於240。 這個指示詞也會使用目前的序言位移，為指定的暫存器產生 `UWOP_SET_FPREG` 回溯程式碼專案。

## <a name="syntax"></a>語法

> **.SETFRAME** *reg*， *offset*

## <a name="remarks"></a>備註

**.SETFRAME**可讓 ml64 使用者指定框架函式回溯的方式，而且只能在序言中使用，這會從[PROC](proc.md)框架宣告延伸至[。ENDPROLOG](dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼;它們只會產生 `.xdata` 和 `.pdata`。 **.SETFRAME**的前面應該會有實際執行要展開之動作的指示。 最好的做法是將回溯指示詞和它們要在宏中回溯的程式碼包裝起來，以確保合約。

如需詳細資訊，請參閱[MASM for x64 （ml64 .exe）](masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>範例

### <a name="description"></a>描述

下列範例顯示如何使用框架指標：

### <a name="code"></a>程式碼

```asm
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

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
