---
title: "嚴重錯誤 C1311 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1311"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1311"
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1311
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

COFF 格式無法以靜態方式初始化 'var' \(位址為 number 位元組\)  
  
 一個在編譯時期不知道其值的位址不能以靜態方式指定給其型別的儲存區小於四位元組的變數。  
  
 這項錯誤可能會發生在其他一切都有效的 C\+\+ 程式碼上。  
  
 下列範例示範了一種可能會造成 C1311 的情況。  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```