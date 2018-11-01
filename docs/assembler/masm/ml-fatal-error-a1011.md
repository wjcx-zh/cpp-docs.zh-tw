---
title: ML 嚴重錯誤 A1011
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 591755a1d7066d8251f61d2a22b9601a9ccb9dcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520194"
---
# <a name="ml-fatal-error-a1011"></a>ML 嚴重錯誤 A1011

**指示詞必須是在控制區塊**

組譯工具找到其中一個不預期的高層級指示詞。 找不到下列指示詞的其中一個：

- [.ELSE](../../assembler/masm/dot-else.md)而不需要[。如果](../../assembler/masm/dot-if.md)

- [.ENDIF](../../assembler/masm/dot-endif.md)而不需要[。如果](../../assembler/masm/dot-if.md)

- [.ENDW](../../assembler/masm/dot-endw.md)而不需要[。WHILE](../../assembler/masm/dot-while.md)

- [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)而不需要[。重複](../../assembler/masm/dot-repeat.md)

- [.繼續](../../assembler/masm/dot-continue.md)而不需要[。雖然](../../assembler/masm/dot-while.md)或[。重複](../../assembler/masm/dot-repeat.md)

- [.中斷](../../assembler/masm/dot-break.md)而不需要[。雖然](../../assembler/masm/dot-while.md)或[。重複](../../assembler/masm/dot-repeat.md)

- [.其他](../../assembler/masm/dot-else.md)下列 `.ELSE`

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>