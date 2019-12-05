---
title: ML 非嚴重錯誤 A2006
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 6c55cb66d6eaeaf620aeedc1dd924f6618cbf817
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856779"
---
# <a name="ml-nonfatal-error-a2006"></a>ML 非嚴重錯誤 A2006

**未定義的符號：識別碼**

嘗試使用未定義的符號。

可能發生下列其中一種情況：

- 未定義符號。

- 欄位不是所指定結構的成員。

- 符號已定義于未包含的 include 檔案中。

- 在沒有[EXTERN](../../assembler/masm/extern-masm.md)或[EXTERNDEF](../../assembler/masm/externdef.md)指示詞的情況下使用了外部符號。

- 符號名稱拼錯。

- 本機程式碼標籤是在其範圍外參考。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>