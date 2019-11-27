---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: b0f047278f6250d5ef359f7992df4ea23f4bbd9b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398039"
---
# <a name="pushframe"></a>.PUSHFRAME

產生 `UWOP_PUSH_MACHFRAME` 回溯程式碼專案。 如果指定了選擇性的程式*代碼*，則回溯程式碼專案會被賦予1的修飾詞。 否則修飾詞為0。

## <a name="syntax"></a>語法

> **.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME** ⟦*碼*⟧;;

## <a name="remarks"></a>備註

.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME 可讓 ml64 使用者指定框架函式回溯的方式，而且只允許在序言中使用，這會從[PROC](../../assembler/masm/proc.md)框架宣告延伸至[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼;它們只會產生 `.xdata` 和 `.pdata`。 **.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME**的前面應該會有實際執行要展開之動作的指示。 最好的做法是將回溯指示詞和它們要在宏中回溯的程式碼包裝起來，以確保合約。

如需詳細資訊，請參閱[MASM for x64 （ml64 .exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)
