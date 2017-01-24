---
title: "&#39;If&#39; 運算元不可以命名為引數。 | Microsoft Docs"
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
  - "bc33105"
  - "vbc33105"
helpviewer_keywords: 
  - "BC33105"
ms.assetid: 596baeb6-a44f-4d92-beb7-06624b60c00d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39; 運算元不可以命名為引數。
`If` 運算子的運算元使用具名引數無效。 下列範例會產生這個錯誤：  
  
```  
Dim i As Integer Dim result As String ' Not valid. ' result = (If(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 這允許具名引數，不同於 `IIf` 函式，如下列程式碼所示：  
  
```  
' Valid. IIf(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 **錯誤識別碼：**BC33105  
  
### 更正這個錯誤  
  
-   移除運算元的名稱指派，如下列程式碼所示。  
  
    ```  
    result = If(i > 0, "positive", "not positive")  
    ```  
  
## 請參閱  
 [If Operator](../Topic/If%20Operator%20\(Visual%20Basic\).md)   
 [Passing Arguments by Position and by Name](../Topic/Passing%20Arguments%20by%20Position%20and%20by%20Name%20\(Visual%20Basic\).md)