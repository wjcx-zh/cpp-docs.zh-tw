---
title: .PUSHFRAME
description: 描述。SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME MASM 指示詞，用來指定如何回溯框架函數。
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 0aaec119d26d87fddb1eba505458da1250a5926e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317574"
---
# <a name="pushframe"></a>.PUSHFRAME

產生 `UWOP_PUSH_MACHFRAME` 回溯程式碼專案。 如果指定了選擇性的**code**關鍵字，則回溯程式碼專案會被賦予1的修飾詞。 否則修飾詞為0。

## <a name="syntax"></a>語法

> **.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME** ⟦**碼**⟧;;

## <a name="remarks"></a>備註

.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME 可讓 ml64 使用者指定框架功能回溯的方式。 只有在序言中才允許，它會從[程式框架宣告](proc.md)延伸至[。ENDPROLOG](dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼;它們只會產生 `.xdata` 和 `.pdata`。 **.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME**的前面應該會有實際執行要展開之動作的指示。 最好的做法是將回溯指示詞和其要在宏中回溯的程式碼包裝起來，以確保合約。

如需詳細資訊，請參閱[MASM for x64 （ml64 .exe）](masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
