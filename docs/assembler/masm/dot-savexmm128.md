---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: c29ec47170c5e0f46f02d53f23ab477a79bbdc32
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507896"
---
# <a name="savexmm128"></a>.SAVEXMM128

會產生其中一個`UWOP_SAVE_XMM128`或`UWOP_SAVE_XMM128_FAR`回溯程式碼項目指定的 XMM 暫存器，並使用目前的序言位移的位移。 MASM 會選擇最有效率的編碼方式。

## <a name="syntax"></a>語法

> .savexmm128 xmmreg、 位移

## <a name="remarks"></a>備註

.SAVEXMM128 允許 ml64.exe 使用者指定框架函式的回溯時，如何，而且只允許在序言，始[PROC](../../assembler/masm/proc.md)框架宣告[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指示詞。 這些指示詞不會產生程式碼路徑。它們只會產生`.xdata`和`.pdata`。 .SAVEXMM128 之前應該加實際實作要回溯動作的指示。 它是個不錯的做法，包裝的回溯程式指示詞和它們以確保協議要在巨集中的回溯程式碼。

*位移*必須是 16 的倍數。

如需詳細資訊，請參閱 < [MASM (ml64.exe) x64 的](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>