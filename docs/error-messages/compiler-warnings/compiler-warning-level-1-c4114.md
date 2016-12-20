---
title: "編譯器警告 (層級 1) C4114 | Microsoft Docs"
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
  - "C4114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4114"
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4114
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

相同型別的限定詞已經使用多次  
  
 型別宣告 \(Type Declaration\) 或定義使用了某個型別限定詞 \(**const**、`volatile`、**signed** 或 `unsigned`\) 一次以上。  在 Microsoft Extensions \(\/Ze\) 中這將產生一個警告，在 ANSI 相容性 \(\/Za\) 之中則會產生一個錯誤。  
  
 下列範例會產生 C4114：  
  
```  
// C4114.cpp  
// compile with: /W1 /c  
volatile volatile int i;   // C4114  
```  
  
 下列範例會產生 C4114：  
  
```  
// C4114_b.cpp  
// compile with: /W1 /c  
static const int const * ii;   // C4114  
static const int * const iii;   // OK  
```