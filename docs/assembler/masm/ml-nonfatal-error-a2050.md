---
title: "ML 非嚴重錯誤 A2050 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2050
dev_langs: C++
helpviewer_keywords: A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a51a90f294afd0347057efb04ab37ce790532ba4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2050"></a>ML 非嚴重錯誤 A2050
**實數或不允許的 BCD 數字**  
  
 浮點數 （實際） 的數字或二進位檔 (BCD) 的自動程式化十進位常數使用為資料的初始設定式。  
  
 發生下列其中一項：  
  
-   在運算式中使用實數或 BCD。  
  
-   實際數字用來初始化指示詞以外[DWORD](../../assembler/masm/dword.md)， [QWORD](../../assembler/masm/qword.md)，或[TBYTE](../../assembler/masm/tbyte.md)。  
  
-   BCD 用來初始化指示詞以外`TBYTE`。  
  
## <a name="see-also"></a>請參閱  
 [ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)