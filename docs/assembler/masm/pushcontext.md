---
title: "PUSHCONTEXT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PUSHCONTEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PUSHCONTEXT directive"
ms.assetid: 18e528ee-df6c-4ce6-8823-b35b40f757fd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# PUSHCONTEXT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

儲存目前的部分或全部`context`： 區段暫存器假設基數值、 清單和 cref 旗標或是處理器\/副處理器的值。  The `context` can be **ASSUMES**, `RADIX`, **LISTING**, **CPU**, or **ALL**.  
  
## 語法  
  
```  
  
PUSHCONTEXT context  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)