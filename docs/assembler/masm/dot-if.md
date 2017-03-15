---
title: ".IF | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".IF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".IF directive"
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .IF
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生測試的程式碼`condition1` \(比方說，AX \> 7\)，並執行*陳述式*如果該條件為真。  
  
## 語法  
  
```  
  
   .IF condition1   
statements  
[[.ELSEIF condition2   
   statements]]  
[[.ELSE  
   statements]]  
.ENDIF  
```  
  
## 備註  
 If a [.其他](../../assembler/masm/dot-else.md)如下所示，其陳述式會執行原始的條件不符合。  請注意在執行階段評估的條件。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)