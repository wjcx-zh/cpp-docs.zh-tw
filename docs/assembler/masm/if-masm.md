---
title: "IF (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IF directive"
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# IF (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

授與組件的 *ifstatements* 如果 *expression1* 則為 true \(非零\) 或 *elseifstatements* 如果 *expression1* 為 false \(0\) 和*表示*為 true。  
  
## 語法  
  
```  
  
   IF expression1  
ifstatements  
[[ELSEIF expression2  
   elseifstatements]]  
[[ELSE  
   elsestatements]]  
ENDIF  
```  
  
## 備註  
 下列指示詞可能會取代 [ELSEIF](../../assembler/masm/elseif-masm.md)：  **ELSEIFB**，  **ELSEIFDEF**，  **ELSEIFDIF**，  **ELSEIFDIFI**，  **ELSEIFE**，  **ELSEIFIDN**，  **ELSEIFIDNI**，  **ELSEIFNB**，以及  **ELSEIFNDEF**。  \(選擇性\) 會組合 *elsestatements* 如果先前的運算式為 false。  請注意，這些運算式會評估在組件的時間。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)