---
title: "編譯器錯誤 C2537 | Microsoft Docs"
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
  - "C2537"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2537"
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2537
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'specifier' : 不合法的連結規格  
  
 可能的原因：  
  
1.  不支援這個連結規範。  僅支援「C」連結規範 \(Linkage Specifier\)。  
  
2.  在一組多載函式中，有一個以上的函式被指定為「C」連結。  這是不允許的。  
  
 下列範例會產生 C2537：  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```