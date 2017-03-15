---
title: "COMM | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COMM"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMM directive"
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# COMM
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用控制台中的屬性建立微乎其微變數`definition`。  
  
## 語法  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## 備註  
 每個`definition`都採用下列格式：  
  
 \[*langtype*\]\]\[**NEAR** &#124; **FAR**\]*label***:**`type`\[**:***count*\]  
  
 *標籤*是變數的名稱。  `type`可以是任何型別規範 \([位元組](../../assembler/masm/byte-masm.md)，  [WORD](../../assembler/masm/word.md)，依此類推\) 或指定的位元組數目的整數。  *計數*指定的數目 \(一個為預設值\) 的資料物件。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)