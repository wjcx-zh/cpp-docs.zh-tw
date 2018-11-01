---
title: PROC
ms.date: 08/30/2018
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: e7931c97570c0fefcacb0123d75934867793fba4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439620"
---
# <a name="proc"></a>PROC

標記開始和結束呼叫的程序區塊*標籤*。 區塊中的陳述式可以呼叫具有**呼叫**指示或[INVOKE](../../assembler/masm/invoke.md)指示詞。

## <a name="syntax"></a>語法

> *標籤*程序 [[*距離*]] [[*langtype*]] [[*可視性*]] [[\<*prologuearg*>]] [[會使用*reglist*]] [[，*參數*[[:*標記*]]]...<br/>
> [[畫面格 [[:*ehandler 位址*]]]]<br/>
> *陳述式*<br/>
> *標籤*ENDP

## <a name="remarks"></a>備註

[[畫面格 [[:*ehandler 位址*]]]] 時才有效 ml64.exe，並造成 MASM.pdata 中產生的函式的資料表項目，並回溯.xdata 中的資訊的函式的結構化例外狀況處理回溯行為。

當**框架**屬性時，它必須接著[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。

請參閱[MASM (ml64.exe) x64 的](../../assembler/masm/masm-for-x64-ml64-exe.md)如需有關使用 ml64.exe。

## <a name="example"></a>範例

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

上述的程式碼會發出下列函式表，並回溯資訊：

```Output
FileHeader->Machine 34404
Dumping Unwind Information for file ex2.exe

.pdata entry 1 0x00001000 0x00001023

  Unwind data: 0x00002000

    Unwind version: 1
    Unwind Flags: None
    Size of prologue: 0x08
    Count of codes: 3
    Frame register: rbp
    Frame offset: 0x0
    Unwind codes:

      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00
      Code offset: 0x05, ALLOC_SMALL, size=0x10
      Code offset: 0x01, PUSH_NONVOL, register=rbp
```

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>