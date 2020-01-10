---
title: .PUSHREG
ms.date: 12/16/2019
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: de6ffd3668f47732144e8c632410f6dfde6b2f31
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318289"
---
# <a name="pushreg"></a>.PUSHREG

使用序言中目前的位移，為指定的暫存器編號產生 `UWOP_PUSH_NONVOL` 回溯程式碼專案。

## <a name="syntax"></a>語法

> .PUSHREG *register*

## <a name="remarks"></a>備註

**.PUSHREG**可讓 ml64 使用者指定框架函式回溯的方式，而且只能在序言中使用，這會從[PROC](proc.md) **框架**宣告延伸至[。ENDPROLOG](dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼;它們只會產生 `.xdata` 和 `.pdata`。 **.PUSHREG**的前面應該會有實際執行要展開之動作的指示。 最好的做法是將回溯指示詞和它們要在宏中回溯的程式碼包裝起來，以確保合約。

*register*可以是下列其中一個： \
RAX |RCX |RDX |RBX |RDI |RSI |RBP |R8 |R9 |R10 |R11 |R12 |R13 |R14 |R15.

如需詳細資訊，請參閱[MASM for x64 （ml64 .exe）](masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>範例

### <a name="description"></a>描述

下列範例示範如何推送非 volatile 暫存器。

### <a name="code"></a>程式碼

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
