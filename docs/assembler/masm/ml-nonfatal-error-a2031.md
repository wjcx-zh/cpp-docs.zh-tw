---
title: "ML Nonfatal Error A2031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2031"
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Nonfatal Error A2031
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**必須是索引或基底暫存器**  
  
 您嘗試使用的暫存器不在記憶體運算式的基底或索引暫存器。  
  
 例如，下列運算式會造成此錯誤：  
  
```  
[ax]  
[bl]  
```  
  
## 請參閱  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)