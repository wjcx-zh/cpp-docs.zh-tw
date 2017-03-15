---
title: "INVOKE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Invoke"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "INVOKE directive"
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# INVOKE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫程序所提供的地址在*運算式*，在堆疊上，或根據語言類型的標準呼叫慣例的暫存器中傳遞的引數。  
  
## 語法  
  
```  
  
INVOKE   
expression [[, arguments]]  
```  
  
## 備註  
 每個引數傳遞至程序可能是運算式、 暫存器組或是位址運算式 \(運算式前面加上`ADDR`\)。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)