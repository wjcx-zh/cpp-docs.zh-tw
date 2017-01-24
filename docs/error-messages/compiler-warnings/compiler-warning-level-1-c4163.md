---
title: "編譯器警告 (層級 1) C4163 | Microsoft Docs"
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
  - "C4163"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4163"
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4163
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 無法當做內建函式使用  
  
 指定的函式不能用作為[內建](../../preprocessor/intrinsic.md)函式。 編譯器會忽略無效的函式名稱。  
  
 下列範例會產生 C4163：  
  
```  
// C4163.cpp // compile with: /W1 /LD #include <math.h> #pragma intrinsic(mysin)   // C4163 // try the following line instead // #pragma intrinsic(sin)  
```