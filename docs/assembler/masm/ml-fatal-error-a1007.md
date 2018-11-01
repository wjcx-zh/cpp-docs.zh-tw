---
title: ML 嚴重錯誤 A1007
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 98933c3a24da22f447174a3b51c4855690aba83e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603394"
---
# <a name="ml-fatal-error-a1007"></a>ML 嚴重錯誤 A1007

**巢狀太深的層級**

「 組合器 」 中，已達到其巢狀的限制。 限制為 20 的層級，除了明，否則。

下列其中一項是巢狀結構太深：

- 高層級的指示詞，例如[。如果](../../assembler/masm/dot-if.md)， [。重複](../../assembler/masm/dot-repeat.md)，或[。雖然](../../assembler/masm/dot-while.md)。

- 結構定義。

- 條件式組件指示詞。

- 程序定義。

- A [PUSHCONTEXT](../../assembler/masm/pushcontext.md) （限制為 10） 的指示詞。

- 區段定義。

- Include 檔。

- 巨集。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>