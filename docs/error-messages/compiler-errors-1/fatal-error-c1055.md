---
title: "嚴重錯誤 C1055 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1055"
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 嚴重錯誤 C1055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制：索引鍵不足  
  
 原始程式檔包含的符號太多。  編譯器用完了符號表的雜湊機碼。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  將原始程式檔分割成較小的檔案。  
  
2.  排除不必要的標頭檔 \(Header File\)。  
  
3.  重複使用暫存和全域變數，而不要建立新的變數。