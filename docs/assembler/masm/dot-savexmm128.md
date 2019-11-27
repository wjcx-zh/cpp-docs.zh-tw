---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 08bc5ab50e15aa59e0c49992d1810c7de20f364e
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397955"
---
# <a name="savexmm128"></a>.SAVEXMM128

使用目前的序言位移，為指定的 XMM 暫存器產生 `UWOP_SAVE_XMM128` 或 `UWOP_SAVE_XMM128_FAR` 回溯程式碼專案，以及位移。 MASM 會選擇最有效率的編碼方式。

## <a name="syntax"></a>語法

> **.SAVEXMM128** *xmmreg* ， *offset*

## <a name="remarks"></a>備註

**.SAVEXMM128**可讓 ml64 使用者指定框架函式回溯的方式，而且只能在序言中使用，這會從[PROC](../../assembler/masm/proc.md)框架宣告延伸至[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼;它們只會產生 `.xdata` 和 `.pdata`。 .SAVEXMM128 的前面應該會有實際執行要展開之動作的指示。 最好的做法是將回溯指示詞和它們要在宏中回溯的程式碼包裝起來，以確保合約。

*offset*必須是16的倍數。

如需詳細資訊，請參閱[MASM for x64 （ml64 .exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)
