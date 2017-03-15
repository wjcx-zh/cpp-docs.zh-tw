---
title: "嚴重錯誤 C1853 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1853"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1853"
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 嚴重錯誤 C1853
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'filename' 先行編譯標頭檔來自較舊版本的編譯器，或者先行編譯標頭檔是用 C\+\+ 撰寫，而您是從 C 使用它 \(反之亦然\)  
  
 可能的原因：  
  
-   先行編譯標頭是用先前版本的編譯器編譯的。  請嘗試使用目前的編譯器重新編譯該標頭。  
  
-   先行編譯標頭是 C\+\+，而您卻從 C 使用該標頭。  請藉由指定其中一個 [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 編譯器選項或將原始程式檔的後置字元變更為 "c"，重新編譯標頭以與 C 搭配使用。  如需詳細資訊，請參閱[先行編譯程式碼的兩個選擇](../../build/reference/two-choices-for-precompiling-code.md)。