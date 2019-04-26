---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 9ea506e25435c5d6f1b10eab8c4f25f72bf88791
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178432"
---
# <a name="pushframe"></a>.PUSHFRAME

會產生`UWOP_PUSH_MACHFRAME`回溯程式碼項目。 如果選擇性`code`指定，則回溯程式碼項目指定為 1 的修飾詞。 否則修飾詞為 0。

## <a name="syntax"></a>語法

> .PUSHFRAME [code]

## <a name="remarks"></a>備註

.PUSHFRAME 允許 ml64.exe 使用者指定框架的函式的回溯時，而且只允許在序言，始[PROC](../../assembler/masm/proc.md)框架宣告[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼路徑。它們只會產生`.xdata`和`.pdata`。 .PUSHFRAME 之前應該加實際實作要回溯動作的指示。 它是個不錯的做法，包裝的回溯程式指示詞和它們以確保協議要在巨集中的回溯程式碼。

如需詳細資訊，請參閱 < [MASM (ml64.exe) x64 的](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>