---
title: "編譯器錯誤 C2002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2002"
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C2002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無效的寬字元常數  
  
 多位元組字元常數無效。  
  
### 若要修正，請檢查下列可能原因  
  
1.  寬字元常數 \(Wide\-Character Constant\) 包含的位元組超出預期。  
  
2.  沒有包含標準的 STDDEF.h 標頭。  
  
3.  寬字元不能與一般的字串常值 \(String Literal\) 串連。  
  
4.  寬字元常數前面必須加上「L」字元：  
  
    ```  
    L'mbconst'  
    ```  
  
5.  對於 Microsoft C\+\+ 而言，前置處理器指示詞的文字引數必須是 ASCII。  舉例來說，指示詞 `#pragma message(L"string")` 無效。