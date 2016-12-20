---
title: "不再使用 &#39;D&#39; 來表示指數，請使用 &#39;E&#39; 代替。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30827"
  - "bc30827"
helpviewer_keywords: 
  - "BC30827"
ms.assetid: 577f8c0b-9e8a-433f-b504-9ddaa936c250
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不再使用 &#39;D&#39; 來表示指數，請使用 &#39;E&#39; 代替。
無法用 'D' 字元表示指數。  
  
 **錯誤識別碼：**BC30827  
  
### 更正這個錯誤  
  
-   請使用 `^` 運算子或 `E+` 字元來表示指數的存在。 例如:  
  
    ```  
    Const Mole = 6.02E+23 ' Same as 6.02D23 Const Mole2 = 6.02 * 10 ^ 23 ' Same as 6.02D23  
    ```  
  
## 請參閱  
 [^ Operator](../Topic/%5E%20Operator%20\(Visual%20Basic\).md)   
 [Numeric Data Types](../Topic/Numeric%20Data%20Types%20\(Visual%20Basic\).md)