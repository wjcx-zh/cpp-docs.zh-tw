---
title: "ML Fatal Error A1010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1010"
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Fatal Error A1010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**不相符的區塊巢狀結構：**  
  
 區塊的開頭，並沒有對應的結尾，或區塊的結尾並沒有相符的開頭。  可能會牽涉到下列其中一項：  
  
-   高層級的指示詞，例如 [。IF](../../assembler/masm/dot-if.md), [.重複](../../assembler/masm/dot-repeat.md)，或  [。雖然](../../assembler/masm/dot-while.md)。  
  
-   組件的條件式指示詞，例如 [IF](../../assembler/masm/if-masm.md)， [重複](../../assembler/masm/repeat.md)，或 **時**。  
  
-   結構或等位定義。  
  
-   程序定義。  
  
-   區段定義。  
  
-   A  [POPCONTEXT](../../assembler/masm/popcontext.md) 指示詞。  
  
-   條件式組件指示詞，例如 [ELSE](../../assembler/masm/else-masm.md)，  [ELSEIF](../../assembler/masm/elseif-masm.md)，或  **ENDIF** 而不要符合  [IF](../../assembler/masm/if-masm.md)。  
  
## 請參閱  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)