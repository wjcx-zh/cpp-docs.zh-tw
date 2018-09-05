---
title: ML 嚴重錯誤 A1011 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1011
dev_langs:
- C++
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32949773b869d189516a381ca7df941760a1e4e4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690804"
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