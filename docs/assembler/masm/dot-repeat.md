---
title: ".REPEAT | Microsoft Docs"
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
  - ".REPEAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".REPEAT directive"
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .REPEAT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會產生重複的區塊中執行的程式碼*陳述式*才`condition`成真。  [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，而成為，則為 true，當 CX 是零，可能會取代  [。等到](../../assembler/masm/dot-until.md)。  `condition`是選擇性的 with  **。UNTILCXZ**。  
  
## 語法  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)