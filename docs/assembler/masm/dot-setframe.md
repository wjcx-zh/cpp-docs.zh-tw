---
title: .SETFRAME
ms.date: 08/30/2018
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: c2c35cdb2889350b27e9fb11c397b684506972c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178172"
---
# <a name="setframe"></a>.SETFRAME

在框架中的填滿註冊中使用指定的暫存器的回溯資訊的欄位和位移 (`reg`) 和位移 (`offset`)。 位移必須是 16 的倍數，且小於或等於 240。 這個指示詞也會產生`UWOP_SET_FPREG`針對指定註冊使用的目前位移，序言回溯程式碼項目。

## <a name="syntax"></a>語法

> .SETFRAME reg 位移

## <a name="remarks"></a>備註

.SETFRAME 允許 ml64.exe 使用者指定框架函式的回溯時，如何，而且只允許在序言，始[PROC](../../assembler/masm/proc.md)框架宣告[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼路徑。它們只會產生`.xdata`和`.pdata`。 .SETFRAME 之前應該加實際實作要回溯動作的指示。 它是個不錯的做法，包裝的回溯程式指示詞和它們以確保協議要在巨集中的回溯程式碼。

如需詳細資訊，請參閱 < [MASM (ml64.exe) x64 的](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>範例

### <a name="description"></a>描述

下列範例示範如何使用框架指標：

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

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>