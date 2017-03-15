---
title: "ML Error Messages | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.errors.ml"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MASM (Microsoft Macro Assembler), ML error messages"
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Error Messages
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MASM 元件所產生的錯誤訊息可分為三類：  
  
-   **嚴重錯誤。** 這些警示表示了嚴重的問題，以致於無法完成一般的程序公用程式。  
  
-   **非嚴重錯誤。** 此公用程式可能會完成其程序。  如果是的話，它的結果不是可能會想的要的。  
  
-   **警告。** 這些訊息指出可能會讓您取得想要的結果的條件。  
  
 所有的錯誤訊息的形式如下：  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 其中：  
  
 `Utility`  
 傳送錯誤訊息的程式。  
  
 *檔名*  
 檔案包含錯誤產生的條件。  
  
 *Line*  
 錯誤狀況的存在的大約行。  
  
 *Error\_type*  
 嚴重錯誤、 錯誤或警告。  
  
 *程式碼*  
 唯一 5 或 6 位數的錯誤代碼。  
  
 `Message_text`  
 短整數和一般錯誤條件的描述。  
  
## 請參閱  
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)