---
title: "編譯器錯誤 C2041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2041"
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不合法的數字 'character' \(對於' number' 進位的數值而言\)  
  
 指定字元對於基底 \(例如八進位或十六進位\) 而言是無效的數字。  
  
 下列範例會產生 C2041：  
  
```  
// C2041.cpp  
int i = 081;   // C2041  8 is not a base 8 digit  
```  
  
 可能的解決方案：  
  
```  
// C2041b.cpp  
// compile with: /c  
int j = 071;  
```