---
title: .ALLOCSTACK
ms.date: 08/30/2018
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: b92db3d03bb5c45e67473cd4085f2369698f6b42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185649"
---
# <a name="allocstack"></a>.ALLOCSTACK

會產生**UWOP_ALLOC_SMALL**或是**UWOP_ALLOC_LARGE**與序言中的目前位移的指定大小。

## <a name="syntax"></a>語法

> .ALLOCSTACK 大小

## <a name="remarks"></a>備註

MASM 會選擇最有效率的編碼方式，就指定大小。

.ALLOCSTACK 允許 ml64.exe 使用者指定框架的函式的回溯時，而且只允許在序言，始[PROC](../../assembler/masm/proc.md)框架宣告[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼路徑。它們只會產生`.xdata`和`.pdata`。 .ALLOCSTACK 之前應該加實際實作要回溯動作的指示。 它是個不錯的做法，包裝的回溯程式指示詞和它們以確保協議要在巨集中的回溯程式碼。

`size`運算元必須是 8 的倍數。

如需詳細資訊，請參閱[MASM (ml64.exe) x64 的](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>範例

下列範例示範如何指定回溯/例外狀況處理常式：

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

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>