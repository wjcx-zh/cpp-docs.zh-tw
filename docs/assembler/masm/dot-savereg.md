---
title: .SAVEREG
ms.date: 12/16/2019
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 18cb6e563084e8c5357bec2a8052a2b38fcdffee
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317548"
---
# <a name="savereg"></a>.SAVEREG

使用目前的序言位移，為指定的暫存器（*reg*）和位移（*offset*）產生 `UWOP_SAVE_NONVOL` 或 `UWOP_SAVE_NONVOL_FAR` 回溯程式碼專案。 MASM 會選擇最有效率的編碼方式。

## <a name="syntax"></a>語法

> **.SAVEREG** *reg* __，__ *offset*

## <a name="remarks"></a>備註

**.SAVEREG**可讓 ml64 使用者指定框架函式回溯的方式，而且只允許在序言中使用，這會從[PROC](proc.md)框架宣告延伸至[。ENDPROLOG](dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼;它們只會產生 `.xdata` 和 `.pdata`。 **.SAVEREG**的前面應該會有實際執行要展開之動作的指示。 最好的做法是將回溯指示詞和它們要在宏中回溯的程式碼包裝起來，以確保合約。

如需詳細資訊，請參閱[MASM for x64 （ml64 .exe）](masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
