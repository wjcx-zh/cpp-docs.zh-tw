---
title: "exit 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exit 函式"
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# exit 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**exit** 函式是在標準 Include 檔案 STDLIB.H 中宣告，此函式會終止 C\+\+ 程式。  
  
 做為引數提供給 **exit** 的值，會傳回作業系統做為程式的傳回碼或結束代碼。  依照慣例，傳回碼為零，表示程式順利完成。  
  
> [!NOTE]
>  您可以使用 STDLIB.H 中定義的常數 `EXIT_FAILURE` 和 `EXIT_SUCCESS`，表示程式成功或失敗。  
  
 從 **main** 函式發出 `return` 陳述式，相當於呼叫 **exit** 函式並使用傳回值做為其引數。  
  
 如需詳細資訊，請參閱《執行階段程式庫參考》中的 [exit](../c-runtime-library/reference/exit-exit-exit.md)。  
  
## 請參閱  
 [程式終止](../cpp/program-termination.md)