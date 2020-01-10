---
title: ML 嚴重錯誤 A1007
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: c9527769e0d9397de90f49cbce98b2cca42bed50
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317119"
---
# <a name="ml-fatal-error-a1007"></a>ML 嚴重錯誤 A1007

**嵌套層級太深**

組合器已達到其嵌套限制。 限制為20個層級，除非另有說明。

下列其中一項已嵌套太深：

- 高階指示詞，例如[。如果](dot-if.md)為，則為[。重複](dot-repeat.md)、或[。WHILE](dot-while.md)。

- 結構定義。

- 條件式元件指示詞。

- 程序定義。

- [PUSHCONTEXT](pushcontext.md)指示詞（限制為10）。

- 區段定義。

- Include 檔案。

- 宏。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](ml-error-messages.md)
