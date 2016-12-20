---
title: "EXTERN (MASM) | Microsoft Docs"
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
  - "extern"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXTERN directive"
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# EXTERN (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義一或多個外部變數、 標籤或呼叫的符號*名稱*型別是`type`。  
  
## 語法  
  
```  
  
   EXTERN [[langtype]] name [[(altid)]] :  
type [[, [[langtype]] name [[(altid)]] :type]]...  
```  
  
## 備註  
 `type`可以是 [ABS](../../assembler/masm/operator-abs.md)，哪一個匯入*名稱*做為常數。  相同的 [EXTRN](../../assembler/masm/extrn.md)。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)