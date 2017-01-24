---
title: "編譯器錯誤 C2482 | Microsoft Docs"
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
  - "C2482"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2482"
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2482
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 不允許 'thread' 資料動態初始化  
  
 以 `thread` 屬性宣告的變數不能使用需要執行階段評估的運算式進行初始化。  需要有靜態運算式，才能初始化 `thread` 資料。  
  
 下列範例會產生 C2482：  
  
```  
// C2482.cpp  
// compile with: /c  
#define Thread __declspec( thread )  
Thread int tls_i = tls_i;   // C2482  
  
int j = j;   // OK in C++; C error  
Thread int tls_i = sizeof( tls_i );   // Okay in C and C++  
```