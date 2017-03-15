---
title: "UNION | Microsoft Docs"
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
  - "union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UNION directive"
ms.assetid: 52504abf-7dc1-47c5-944c-b886803a0c6a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# UNION
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

宣告一個或多個資料型別的等位。  *Fielddeclarations* 必須是有效的資料定義。  省略[結束](../../assembler/masm/ends-masm.md) *名稱* 上的標籤巢狀結構 **等位**定義。  
  
## 語法  
  
```  
  
      name   
      UNION [[alignment]] [[, NONUNIQUE]]  
   fielddeclarations  
[[name]] ENDS  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)