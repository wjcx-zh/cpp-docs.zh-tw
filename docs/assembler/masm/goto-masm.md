---
title: "GOTO (MASM) | Microsoft Docs"
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
  - "goto"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GOTO directive"
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# GOTO (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將組件轉移到行相鄰 **：***macrolabel*。  
  
## 語法  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## 備註  
 **移至** 只允許在 [巨集](../../assembler/masm/macro.md)， [的](../../assembler/masm/for-masm.md)，  [FORC](../../assembler/masm/forc.md)， [重複](../../assembler/masm/repeat.md)，以及 **時**區塊。  標籤必須是該行的唯一指示詞，而且必須加上前置字元的冒號。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)