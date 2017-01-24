---
title: "以單一類型規範來宣告多個變數時不允許明確初始化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30671"
  - "vbc30671"
helpviewer_keywords: 
  - "BC30671"
ms.assetid: 57bbdd58-b58d-4144-8fa6-366a7167df27
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 以單一類型規範來宣告多個變數時不允許明確初始化
在同一行中宣告多個變數時，不允許初始化。  
  
 **錯誤識別碼：**BC30671  
  
### 更正這個錯誤  
  
1.  分別宣告及初始化每個項目。  
  
2.  同時宣告多個項目，再初始化每個項目，例如：  
  
    ```  
    Dim x, b, i As Integer x = 9 : b = 9 : i = 9 ' ":" is the same as a new line.  
    ```  
  
## 請參閱  
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [變數宣告](../Topic/Variable%20Declaration%20in%20Visual%20Basic.md)