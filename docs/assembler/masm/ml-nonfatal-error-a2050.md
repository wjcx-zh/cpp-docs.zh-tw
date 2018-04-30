---
title: ML 非嚴重錯誤 A2050 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 159ed131c13166435114234b3b16a82cd4d41d1f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2050"></a>ML 非嚴重錯誤 A2050
**實數或不允許的 BCD 數字**  
  
 浮點數 （實際） 的數字或二進位檔 (BCD) 的自動程式化十進位常數使用為資料的初始設定式。  
  
 發生下列其中一項：  
  
-   在運算式中使用實數或 BCD。  
  
-   實際數字用來初始化指示詞以外[DWORD](../../assembler/masm/dword.md)， [QWORD](../../assembler/masm/qword.md)，或[TBYTE](../../assembler/masm/tbyte.md)。  
  
-   BCD 用來初始化指示詞以外`TBYTE`。  
  
## <a name="see-also"></a>另請參閱  
 [ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)