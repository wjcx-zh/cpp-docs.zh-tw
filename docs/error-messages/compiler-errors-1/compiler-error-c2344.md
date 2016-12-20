---
title: "編譯器錯誤 C2344 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2344"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2344"
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2344
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

align\(\#\): 使用 align 規範必須是 2 的乘冪  
  
 使用 [align](../../cpp/align-cpp.md) 關鍵字時，您傳遞的值必須是 2 的乘冪。  
  
 例如，下列程式碼會產生 C2344，因為 3 不是 2 的乘冪：  
  
```  
// C2344.cpp // compile with: /c __declspec(align(3)) int a;   // C2344 __declspec(align(4)) int b;   // OK  
```