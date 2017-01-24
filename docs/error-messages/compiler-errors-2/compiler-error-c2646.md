---
title: "編譯器錯誤 C2646 | Microsoft Docs"
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
  - "C2646"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2646"
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2646
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

位於全域或命名空間範圍的匿名結構或等位必須宣告為 static  
  
 位於全域或命名空間範圍但未宣告為 `static` 的匿名結構或等位。  
  
 下列範例會產生 C2646，並示範如何修正此問題。  
  
```  
// C2646.cpp  
// compile with: /c  
union { int i; };   // C2646 not static  
  
// OK  
static union { int j; };  
union U { int i; };  
```