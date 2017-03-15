---
title: "編譯器錯誤 C2159 | Microsoft Docs"
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
  - "C2159"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2159"
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2159
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已經指定一個以上的儲存類別  
  
 一個宣告包含多個儲存類別。  
  
 下列範例會產生 C2159：  
  
```  
// C2159.cpp // compile with: /c static int i;   // OK extern static int i;   // C2159  
```