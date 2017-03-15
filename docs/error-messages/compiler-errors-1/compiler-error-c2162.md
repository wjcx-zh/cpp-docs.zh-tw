---
title: "編譯器錯誤 C2162 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2162"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2162"
ms.assetid: 34923628-d35e-48ab-9072-b95e3b5f6b45
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2162
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

必須是巨集型式參數  
  
 跟在字串化運算子 \(\#\) 之後的語彙基元不是型式參數名稱。  
  
## 範例  
 下列範例會產生 C2162：  
  
```  
// C2162.cpp  
// compile with: /c  
#include <stdio.h>  
  
#define print(a) printf_s(b)   // OK  
#define print(a) printf_s(#b)    // C2162  
```