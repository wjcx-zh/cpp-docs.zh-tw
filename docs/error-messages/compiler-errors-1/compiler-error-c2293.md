---
title: "編譯器錯誤 C2293 | Microsoft Docs"
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
  - "C2293"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2293"
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2293
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 將 \_\_based 規範作為成員變數不合法  
  
 `__based` 修飾詞的規範必須是非成員的指標。  
  
 下列範例會產生 C2293：  
  
```  
// C2293.cpp // compile with: /c class A { static int *i; void __based(i) *bp;   // C2293 void *bp2;   // OK };  
```