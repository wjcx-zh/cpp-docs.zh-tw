---
title: "編譯器錯誤 C2735 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2735"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2735"
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2735
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在型式參數型別規範中不允許 'keyword' 關鍵字  
  
 關鍵字在此內容中是無效的。  
  
 下列範例會產生 C2735：  
  
```  
// C2735.cpp  
void f(inline int){}   // C2735  
```