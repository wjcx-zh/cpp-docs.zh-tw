---
title: ML 嚴重錯誤 A1010
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: 6ec82f7f6d559d977a9aa039ed91689a0ef4d49a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856874"
---
# <a name="ml-fatal-error-a1010"></a>ML 嚴重錯誤 A1010

**不相符的區塊嵌套：**

區塊開頭沒有相符的結尾，或區塊結尾沒有相符的開始。 可能牽涉到下列其中一項：

- 高階指示詞，例如[。如果](../../assembler/masm/dot-if.md)為，則為[。重複](../../assembler/masm/dot-repeat.md)、或[。WHILE](../../assembler/masm/dot-while.md)。

- 條件式元件指示詞，例如[IF](../../assembler/masm/if-masm.md)、 [REPEAT](../../assembler/masm/repeat.md)或**WHILE**。

- 結構或等位定義。

- 程序定義。

- 區段定義。

- [POPCONTEXT](../../assembler/masm/popcontext.md)指示詞。

- 條件式元件指示詞，例如[ELSE](../../assembler/masm/else-masm.md)、 [ELSEIF](../../assembler/masm/elseif-masm.md)或**ENDIF** ，但不含符合的[IF](../../assembler/masm/if-masm.md)。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>