---
title: "資源編譯器錯誤 RC2001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2001"
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 資源編譯器錯誤 RC2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

常數中包含新行字元  
  
 繼續的字串常數第二行沒有反斜線 \(**\\**\) 或左右雙引號 \(**"**\)。  
  
 若要將原始程式檔中的字串常數分成兩行，請執行下列任一項：  
  
-   在第一行的行尾加上行接續字元 \(Line\-Continuation Character\)，也就是反斜線。  
  
-   利用雙引號來結束第一行的字串，然後利用另一個引號來開啟下一行的字串。  
  
 在字串常數中內嵌新行字元的逸出序列 \(Escape Sequence\) \(\\n\)，並不足以結束第一行。