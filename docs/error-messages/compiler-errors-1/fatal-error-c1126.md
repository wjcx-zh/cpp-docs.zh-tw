---
title: "嚴重錯誤 C1126 | Microsoft Docs"
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
  - "C1126"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1126"
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1126
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

自動配置超過 size  
  
 函式的本機變數之配置空間 \(加上編譯器所使用的有限空間，例如，用於可切換函式的額外 20 個位元組\) 超過了限制值。  
  
 若要修正這項錯誤，請使用 `malloc` 或 `new`，以配置大量資料。