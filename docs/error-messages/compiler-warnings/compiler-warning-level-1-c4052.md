---
title: "編譯器警告 (層級 1) C4052 | Microsoft Docs"
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
  - "C4052"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4052"
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4052
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函式宣告不同; 一個包含變數引數  
  
 函式的一個宣告未包含變數引數。 會忽略此項。  
  
 下列範例會產生 C4052：  
  
```  
// C4052.c // compile with: /W4 /c int f(); int f(int i, ...);   // C4052  
```