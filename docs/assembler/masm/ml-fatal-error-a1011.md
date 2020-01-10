---
title: ML 嚴重錯誤 A1011
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 5607d6d56e0b3889332dcf2624d519529819b1c9
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318070"
---
# <a name="ml-fatal-error-a1011"></a>ML 嚴重錯誤 A1011

**指示詞必須在控制區塊中**

組合器找到高階指示詞，其中一個不是預期的。 找到下列其中一個指示詞：

- [.否則](dot-else.md)不含[。IF](dot-if.md)

- [.](dot-endif.md)不含[的 ENDIF。IF](dot-if.md)

- [.](dot-endw.md)不含[的 .endw。WHILE](dot-while.md)

- [.](dot-untilcxz.md)不含[的 .untilcxz。重複](dot-repeat.md)

- [.繼續](dot-continue.md)但不執行[。WHILE](dot-while.md)或[。重複](dot-repeat.md)

- [.](dot-break.md)不中斷[。WHILE](dot-while.md)或[。重複](dot-repeat.md)

- [.或者](dot-else.md)，遵循 `.ELSE`

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](ml-error-messages.md)
