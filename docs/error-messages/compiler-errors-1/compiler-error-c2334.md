---
title: "編譯器錯誤 C2334 | Microsoft Docs"
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
  - "C2334"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2334"
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2334
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 ': 或 {' 之前有未預期的語彙基元；略過函式主體  
  
 下列範例會產生 C2334。  以下錯誤會在錯誤 C2059 之後發生：  
  
```  
// C2334.cpp  
// compile with: /c  
// C2059 expected  
struct s1 {  
   s1   {}   // C2334  
   s1() {}   // OK  
};  
```