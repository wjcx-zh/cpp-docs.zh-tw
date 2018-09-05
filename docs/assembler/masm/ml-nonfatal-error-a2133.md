---
title: ML 非嚴重錯誤 A2133 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2133
dev_langs:
- C++
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0df094f5e7135ffb3b9a5f09383e03e411755de3
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678062"
---
# <a name="ml-nonfatal-error-a2133"></a>ML 非嚴重錯誤 A2133

**註冊叫用覆寫的值**

暫存器做為引數傳遞至程序，但產生的程式碼[INVOKE](../../assembler/masm/invoke.md)傳遞其他引數被終結的暫存器的內容。

AX、 AL、 AH、 EAX、 DX、 DL、 DH 及 EDX 暫存器可能使用組合器，來執行資料轉換。

使用不同的註冊。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>