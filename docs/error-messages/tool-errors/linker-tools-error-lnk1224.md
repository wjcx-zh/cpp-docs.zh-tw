---
title: "連結器工具錯誤 LNK1224 | Microsoft Docs"
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
  - "LNK1224"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1224"
ms.assetid: e190b5d0-ce0c-4f65-8cc0-753f1cc9758a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1224
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無效的映像基底 address  
  
 您為映像指定的基底位址 \(Base Address\) 無效。  基底位址必須是 64KB 對齊的 \(最後四個十六進位數必須為零\)，而映像基底大小必須能放入 32 位元 signed 或 unsigned 值之內。