---
title: "編譯器警告 (層級 4) C4152 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4152"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4152"
ms.assetid: 6025ab70-d7cf-4730-913a-3ca0b1186a3a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 4) C4152
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非標準的擴充，運算式中函式\/資料的指標轉換  
  
 函式指標會轉換成資料指標，反之亦然。 Microsoft 擴充功能 \(\/Ze\) 下允許這項轉換，但 ANSI C 下則不允許。