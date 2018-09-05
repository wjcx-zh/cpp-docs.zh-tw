---
title: ML 非嚴重錯誤 A2050 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd2e0e6c2fc818ef9286fd303c07a26bdd8b4e5a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680667"
---
# <a name="ml-nonfatal-error-a2050"></a>ML 非嚴重錯誤 A2050

**實際或不允許的 BCD 數字**

浮點數 （實際） 的數字或二進碼十進位 (BCD) 常數以外的其他用做資料初始設定式。

發生下列其中一項：

- 在運算式中使用實數或 BCD。

- 實際數字用來初始化一個指示詞以外[DWORD](../../assembler/masm/dword.md)， [QWORD](../../assembler/masm/qword.md)，或[TBYTE](../../assembler/masm/tbyte.md)。

- BCD 會用來初始化一個指示詞以外`TBYTE`。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>