---
title: .SAVEREG
ms.date: 08/30/2018
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 324cf0e70a7ad619e5741c9acc18c24a72f54d13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397960"
---
# <a name="savereg"></a>.SAVEREG

使用目前的序言位移，為指定的暫存器（*reg*）和位移（*offset*）產生 `UWOP_SAVE_NONVOL` 或 `UWOP_SAVE_NONVOL_FAR` 回溯程式碼專案。 MASM 會選擇最有效率的編碼方式。

## <a name="syntax"></a>語法

> **.SAVEREG** *reg* __，__ *offset*

## <a name="remarks"></a>備註

**.SAVEREG**可讓 ml64 使用者指定框架函式回溯的方式，而且只允許在序言中使用，這會從[PROC](../../assembler/masm/proc.md)框架宣告延伸至[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼;它們只會產生 `.xdata` 和 `.pdata`。 **.SAVEREG**的前面應該會有實際執行要展開之動作的指示。 最好的做法是將回溯指示詞和它們要在宏中回溯的程式碼包裝起來，以確保合約。

如需詳細資訊，請參閱[MASM for x64 （ml64 .exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)
