---
title: ML 嚴重錯誤 A1011
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 0d8d3896f7788aa3f51605651ee1b728b0e1d60a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856848"
---
# <a name="ml-fatal-error-a1011"></a>ML 嚴重錯誤 A1011

**指示詞必須在控制區塊中**

組合器找到高階指示詞，其中一個不是預期的。 找到下列其中一個指示詞：

- [.否則](../../assembler/masm/dot-else.md)不含[。IF](../../assembler/masm/dot-if.md)

- [.](../../assembler/masm/dot-endif.md)不含[的 ENDIF。IF](../../assembler/masm/dot-if.md)

- [.](../../assembler/masm/dot-endw.md)不含[的 .endw。WHILE](../../assembler/masm/dot-while.md)

- [.](../../assembler/masm/dot-untilcxz.md)不含[的 .untilcxz。重複](../../assembler/masm/dot-repeat.md)

- [.繼續](../../assembler/masm/dot-continue.md)但不執行[。WHILE](../../assembler/masm/dot-while.md)或[。重複](../../assembler/masm/dot-repeat.md)

- [.](../../assembler/masm/dot-break.md)不中斷[。WHILE](../../assembler/masm/dot-while.md)或[。重複](../../assembler/masm/dot-repeat.md)

- [.或者](../../assembler/masm/dot-else.md)，遵循 `.ELSE`

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>