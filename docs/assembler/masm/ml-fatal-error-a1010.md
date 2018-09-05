---
title: ML 嚴重錯誤 A1010 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12b7e8698951e8ef59e0433134ec992af5d5f77f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676293"
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