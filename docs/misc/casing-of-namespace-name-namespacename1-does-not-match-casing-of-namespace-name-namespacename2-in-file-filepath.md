---
title: "命名空間名稱 &#39;&lt;命名空間名稱1&gt;&#39; 的大小寫不符合檔案 &#39;&lt;檔案路徑&gt;&#39; 的命名空間名稱 &#39;&lt;命名空間名稱2&gt;&#39; 的大小寫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40055"
  - "bc40055"
helpviewer_keywords: 
  - "BC40055"
ms.assetid: adaac2fe-1513-4234-afe7-633a76089f36
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 命名空間名稱 &#39;&lt;命名空間名稱1&gt;&#39; 的大小寫不符合檔案 &#39;&lt;檔案路徑&gt;&#39; 的命名空間名稱 &#39;&lt;命名空間名稱2&gt;&#39; 的大小寫
命名空間在專案中出現多次，但大小寫都不一樣。  
  
 *大小寫*是指程式設計項目名稱的大寫和小寫字元。 Visual Basic 不區分大小寫，但是 Common Language Runtime \(CLR\) 區分大小寫。 如需詳細資訊，請參閱 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md) 中的＜名稱區分大小寫＞。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID：**BC40055  
  
### 更正這個錯誤  
  
-   為求安全起見，命名空間的每個參考請一律使用相同的大小寫。 這可以避免 Common Language Runtime 的錯譯。  
  
## 請參閱  
 [Namespace Statement](../Topic/Namespace%20Statement.md)   
 [Visual Basic 中的命名空間](../Topic/Namespaces%20in%20Visual%20Basic.md)   
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Visual Basic Naming Conventions](../Topic/Visual%20Basic%20Naming%20Conventions.md)