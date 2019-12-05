---
title: ML 非嚴重錯誤 A2050
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 15c6449ff4207c92dee28120d4f61be641cf01c8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856573"
---
# <a name="ml-nonfatal-error-a2050"></a>ML 非嚴重錯誤 A2050

**不允許實數或 BCD 號碼**

使用浮點（實數）數位或二進位編碼的十進位（BCD）常數，而非做為資料初始化運算式。

發生下列其中一種情況：

- 運算式中使用了實數或 BCD。

- 實際數位是用來初始化[DWORD](../../assembler/masm/dword.md)、 [QWORD](../../assembler/masm/qword.md)或[TBYTE](../../assembler/masm/tbyte.md)以外的指示詞。

- BCD 是用來初始化 `TBYTE`以外的指示詞。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>