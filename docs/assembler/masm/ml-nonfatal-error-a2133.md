---
title: ML 非嚴重錯誤 A2133
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: c2d13aefe02543129340bcc307771a1026776d61
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854611"
---
# <a name="ml-nonfatal-error-a2133"></a>ML 非嚴重錯誤 A2133

**INVOKE 所覆寫的 register 值**

暫存器已當做引數傳遞至程式，但由[INVOKE](../../assembler/masm/invoke.md)產生的程式碼傳遞其他引數，以終結暫存器的內容。

組合語言可能會使用 AX、AL、AH、EAX、DX、DL、DH 和 EDX 暫存器來執行資料轉換。

使用不同的註冊。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>