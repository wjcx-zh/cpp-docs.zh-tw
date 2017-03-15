---
title: "編譯器警告 (層級 1) C4153 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4153"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4153"
ms.assetid: 37a15754-9dba-470b-adda-c4b888064b3e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4153
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

運算式中函式\/資料的指標轉換  
  
 函式指標會轉換成資料指標，反之亦然。 Microsoft 擴充功能 \(\/Ze\) 下允許這項轉換，但 ANSI C 下則不允許。