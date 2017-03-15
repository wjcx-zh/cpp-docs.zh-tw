---
title: "連結器工具警告 LNK4071 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4071"
ms.assetid: 803f8c34-8219-4f55-a4ae-7133ceff2ba3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具警告 LNK4071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法在後續的連結上累加連結  
  
 LINK 找到一個或多個符號的多個定義，但仍忽略此錯誤，而使用 [\/FORCE](../../build/reference/force-force-file-output.md) 或 **\/FORCE:MULTIPLE** 建立了輸出檔。  LINK 會刪除累加 \(Incremental\) 狀態檔 \(.ilk\)。