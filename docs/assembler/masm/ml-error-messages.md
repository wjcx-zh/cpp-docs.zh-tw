---
title: ML 錯誤訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fbc2ae6388ad11a411850d03de421d2f6820fc03
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="ml-error-messages"></a>ML 錯誤訊息
MASM 元件所產生的錯誤訊息可分成三個類別：  
  
-   **嚴重錯誤。** 這些資訊表示嚴重問題，防止此公用程式完成其一般程序。  
  
-   **非嚴重錯誤。** 此公用程式可能會完成其處理程序。 如果是的話，不可能會想的要其結果。  
  
-   **此警告。** 這些訊息表示您可能無法取得您想要的結果的條件。  
  
 所有的錯誤訊息的形式如下：  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 其中：  
  
 `Utility`  
 傳送錯誤訊息程式。  
  
 *檔案名稱*  
 包含產生錯誤的條件的檔案。  
  
 *程式碼*  
 錯誤狀況存在的大約行。  
  
 *Error_type*  
 嚴重錯誤、 錯誤或警告。  
  
 *程式碼*  
 唯一 5 或 6 位數錯誤程式碼。  
  
 `Message_text`  
 短期與一般錯誤條件的描述。  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft 巨集組譯工具參考](../../assembler/masm/microsoft-macro-assembler-reference.md)