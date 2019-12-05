---
title: ML 嚴重錯誤 A1007
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 01633b4fa084b7d5e14af5a5c6e51e3dca684d2a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856913"
---
# <a name="ml-fatal-error-a1007"></a>ML 嚴重錯誤 A1007

**嵌套層級太深**

組合器已達到其嵌套限制。 限制為20個層級，除非另有說明。

下列其中一項已嵌套太深：

- 高階指示詞，例如[。如果](../../assembler/masm/dot-if.md)為，則為[。重複](../../assembler/masm/dot-repeat.md)、或[。WHILE](../../assembler/masm/dot-while.md)。

- 結構定義。

- 條件式元件指示詞。

- 程序定義。

- [PUSHCONTEXT](../../assembler/masm/pushcontext.md)指示詞（限制為10）。

- 區段定義。

- Include 檔案。

- 宏。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>