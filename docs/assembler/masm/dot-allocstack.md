---
title: .ALLOCSTACK
ms.date: 12/17/2019
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: bcc94619dfa24ab5c8b5d23a60825641290ef176
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314181"
---
# <a name="allocstack"></a>.ALLOCSTACK

產生序言中目前位移之指定大小的**UWOP_ALLOC_SMALL**或**UWOP_ALLOC_LARGE** 。

## <a name="syntax"></a>語法

> **.ALLOCSTACK** *大小*

## <a name="remarks"></a>備註

MASM 會針對指定的大小選擇最有效率的編碼方式。

**.ALLOCSTACK**可讓 ml64 使用者指定框架函式回溯的方式，而且只允許在序言中使用，這會從[PROC](proc.md)框架宣告延伸至[。ENDPROLOG](dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼;它們只會產生 `.xdata` 和 `.pdata`。 **.ALLOCSTACK**的前面應該會有實際執行要展開之動作的指示。 最好的做法是將回溯指示詞和它們要在宏中回溯的程式碼包裝起來，以確保合約。

*大小*運算元必須是8的倍數。

如需詳細資訊，請參閱[MASM for x64 （ml64 .exe）](masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>範例

下列範例顯示如何指定回溯/例外狀況處理常式：

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
