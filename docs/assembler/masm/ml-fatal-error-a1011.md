---
title: "ML Fatal Error A1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1011"
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Fatal Error A1011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**指示詞必須在控制區**  
  
 組譯工具找到未預期的高階指示詞。  找不到下列的指示詞其中一項：  
  
-   [.其他](../../assembler/masm/dot-else.md) 而不  [。如果](../../assembler/masm/dot-if.md)  
  
-   [.ENDIF](../../assembler/masm/dot-endif.md) 而不 [。如果](../../assembler/masm/dot-if.md)  
  
-   [.ENDW](../../assembler/masm/dot-endw.md) 而不 [。雖然](../../assembler/masm/dot-while.md)  
  
-   [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md) 而不 [。重複](../../assembler/masm/dot-repeat.md)  
  
-   [.繼續](../../assembler/masm/dot-continue.md) 而不  [。WHILE](../../assembler/masm/dot-while.md) or [.重複](../../assembler/masm/dot-repeat.md)  
  
-   [.中斷](../../assembler/masm/dot-break.md) 而不  [。WHILE](../../assembler/masm/dot-while.md) or [.重複](../../assembler/masm/dot-repeat.md)  
  
-   [.其他](../../assembler/masm/dot-else.md)下`.ELSE`  
  
## 請參閱  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)