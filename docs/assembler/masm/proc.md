---
title: PROC
ms.date: 12/06/2019
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: 85d9a1e82eebcd83cb0f12f5ca751ec9415af18d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318666"
---
# <a name="proc"></a>PROC

標記名為*label*的程式區塊的開始和結束。 您可以使用**CALL**指令或[INVOKE](invoke.md)指示詞來呼叫區塊中的語句。

## <a name="syntax"></a>語法

> *標籤* **PROC** ⟦*距離*⟧ *⟦ language-類型*⟧⟦ **PUBLIC** | **私**用 | **EXPORT** ⟧⟦ __\<__ *prologuearg* __>__ ⟧⟦**使用** *reglist*⟧⟦ __，__ *parameter* ⟦ __：__ *tag*⟧ .。。⟧\
> ⟦**框架**⟦ __：__ *ehandler-address*⟧⟧ \
> *語句*\
> *標籤* **ENDP**

## <a name="remarks"></a>備註

⟦*距離*⟧和⟦*語言類型*⟧引數只在32位 MASM 中有效。

⟦**FRAME** ⟦ __：__ *ehandler-address*⟧⟧只適用于 ml64，並使 MASM 在中產生函數資料表專案。 pdata 中的 .xdata 和回溯資訊會處理回溯行為。

使用**FRAME**屬性時，其後面必須接著[。ENDPROLOG](dot-endprolog.md)指示詞。

如需使用 ml64 的詳細資訊，請參閱[MASM for x64 （ml64 .exe）](masm-for-x64-ml64-exe.md) 。

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

上述程式碼會發出下列函數資料表和回溯資訊：

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

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
