---
title: ML 非嚴重錯誤 A2050
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 311aedd0cc739fd862efb0a18cc444b3fb75b165
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316976"
---
# <a name="ml-nonfatal-error-a2050"></a>ML 非嚴重錯誤 A2050

**不允許實數或 BCD 號碼**

使用浮點（實數）數位或二進位編碼的十進位（BCD）常數，而非做為資料初始化運算式。

發生下列其中一種情況：

- 運算式中使用了實數或 BCD。

- 實際數位是用來初始化[DWORD](dword.md)、 [QWORD](qword.md)或[TBYTE](tbyte.md)以外的指示詞。

- BCD 是用來初始化 `TBYTE`以外的指示詞。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](ml-error-messages.md)
