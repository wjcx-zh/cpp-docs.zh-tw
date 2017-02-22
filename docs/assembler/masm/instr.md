---
title: "INSTR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InStr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "INSTR directive"
ms.assetid: fc37f6a2-3c95-47b2-b6bb-1066edd25994
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# INSTR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找第一個出現位置 *textitem2* 在 *textitem1*。  
  
## 語法  
  
```  
  
name  
 INSTR [[position,]] textitem1, textitem2  
```  
  
## 備註  
 開始*位置*是選擇性的。  每個文字項目可以是常值字串常數，前面加上`%`，或巨集函式所傳回的字串。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)