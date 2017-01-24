---
title: "編譯器錯誤 C2279 | Microsoft Docs"
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
  - "C2279"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2279"
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2279
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

例外狀況規格不能出現在 typedef 宣告中  
  
 在 **\/Za** 下，typedef 宣告中不允許有[例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)。  
  
 下列範例會產生 C2279：  
  
```  
// C2279.cpp  
// compile with: /Za /c  
typedef int (*xy)() throw(...);   // C2279  
typedef int (*xyz)();   // OK  
```