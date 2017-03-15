---
title: "編譯器警告 C4746 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# 編譯器警告 C4746
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\<expression\>' 的暫時性存取受限於 \/volatile:\[iso&#124;ms\] 設定；請考慮使用 \_\_iso\_volatile\_load\/store 內建函式。  
  
 每當 volatile 變數直接存取時C4746 會散發。  可協助開發人員識別受目前指定的特定 Volatile 模型的影響 \(可以控制與 [\/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) 編譯器選項\) 的程式碼位置。  特別是，當使用 \/volatile:ms 時，幫助定位編譯器產生的硬體記憶體屏障。  
  
 \_\_iso\_volatile\_load\/store 內建可用來明確存取動態記憶體，而不會影響 Volatile 模型的。  使用這些內建函式不會觸發 C4746。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。