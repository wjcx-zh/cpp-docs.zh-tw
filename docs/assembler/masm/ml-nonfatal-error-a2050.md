---
title: ML 非嚴重錯誤 A2050
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 59d08b9c2743a3b45633527bcc54b3e1c4d6a58c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177548"
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