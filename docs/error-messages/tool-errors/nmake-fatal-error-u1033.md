---
title: "NMAKE 嚴重錯誤 U1033 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1033"
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 嚴重錯誤 U1033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤: 未預期的 'string'  
  
 此字串不是 Makefile 的有效語法部分。  
  
### 若要修正，請檢查下列可能原因  
  
1.  如果內嵌 \(Inline\) 檔的封閉的角括弧組 \(**\<\<**\) 不在行首，將發生下列錯誤：  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  如果 Makefile 中的巨集定義包含了等號 \(**\=**\) 但卻沒有前置名稱，或是定義的名稱為展開後沒有任何字元的巨集，將發生下列錯誤：  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  如果 TOOLS.INI 的註解行中的分號 \(**;**\) 不在行首，將發生下列錯誤：  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  如果 Makefile 已由文書處理器格式化，將發生下列錯誤：  
  
    ```  
    syntax error : ':' unexpected  
    ```