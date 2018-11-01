---
title: ML 嚴重錯誤 A1010
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: eb4d77b856e93a8d64ee6c51bec63ceae59b22e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449123"
---
# <a name="ml-fatal-error-a1010"></a>ML 嚴重錯誤 A1010

**不相符的區塊的巢狀結構：**

區塊開頭沒有對應的結尾，或區塊結尾沒有相符的開頭。 可能會牽涉到下列其中一項：

- 高層級的指示詞，例如[。如果](../../assembler/masm/dot-if.md)， [。重複](../../assembler/masm/dot-repeat.md)，或[。雖然](../../assembler/masm/dot-while.md)。

- 這類的條件式組件指示詞[IF](../../assembler/masm/if-masm.md)，[重複](../../assembler/masm/repeat.md)，或**雖然**。

- 結構或等位的定義。

- 程序定義。

- 區段定義。

- A [POPCONTEXT](../../assembler/masm/popcontext.md)指示詞。

- 條件式組件指示詞，例如[ELSE](../../assembler/masm/else-masm.md)， [ELSEIF](../../assembler/masm/elseif-masm.md)，或**ENDIF**但沒有相符[如果](../../assembler/masm/if-masm.md)。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>