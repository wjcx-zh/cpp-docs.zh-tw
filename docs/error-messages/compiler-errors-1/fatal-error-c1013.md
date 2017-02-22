---
title: "嚴重錯誤 C1013 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1013"
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 嚴重錯誤 C1013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制 : 左括號太多，請簡化運算式或分為數個陳述式  
  
 運算式中包含對單一運算式而言太多的括弧層級。 請簡化運算式，或將它切為多個陳述式。  
  
 在 Visual C\+\+ 6.0 Service Pack 3 之前，對於單一運算式中的巢狀括弧限制是 59。 目前巢狀括弧的限制為 256。