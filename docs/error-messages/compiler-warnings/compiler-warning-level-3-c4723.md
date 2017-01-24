---
title: "編譯器警告 (層級 3) C4723 | Microsoft Docs"
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
  - "C4723"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4723"
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4723
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可能除以 0  
  
 除法運算式中的第二個運算元在編譯時被評估為零，產生未定義的結果。  
  
 只有在使用 [\/Og](../../build/reference/og-global-optimizations.md) 或應用 \/Og 的最佳化選項時才會發出此警告。  
  
 編譯器可能已產生零運算元。