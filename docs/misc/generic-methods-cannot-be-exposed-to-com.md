---
title: "泛型方法不可以公開至 COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30943"
  - "bc30943"
helpviewer_keywords: 
  - "BC30943"
ms.assetid: 0e3bff62-f187-4864-8520-70f6be22e869
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 泛型方法不可以公開至 COM
包含一或多個泛型程序的 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 元件匯出至 COM 元件。  
  
 元件物件模型 \(COM\) 不支援泛型類型，而且無法與它們交互操作。  
  
 **錯誤 ID︰**BC30943  
  
### 更正這個錯誤  
  
-   請從 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 元件中移除泛型程序，或不要將它用於 COM Interop。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [COM Interop](../Topic/COM%20Interop%20\(Visual%20Basic\).md)