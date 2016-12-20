---
title: "條件式編譯運算式中不允許可為 Null 的類型 | Microsoft Docs"
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
  - "bc33111"
  - "vbc33111"
helpviewer_keywords: 
  - "BC33111"
ms.assetid: 2c2587e5-2179-4a31-bcf7-7004db6f2d73
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 條件式編譯運算式中不允許可為 Null 的類型
條件式編譯指示詞的運算式中無法使用可為 Null 的類型。 例如，下列程式碼會造成這個錯誤。  
  
```vb#  
'#Const triggerPoint = 0 '' Not valid. '#If CType(triggerpoint, Boolean?) = True Then '        ' Body of the conditional directive. '#End If  
```  
  
 **錯誤 ID：**BC33111  
  
### 更正這個錯誤  
  
-   請移除可為 Null 的類型指定。  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)   
 [\#If...Then...\#Else Directives](../Topic/%23If...Then...%23Else%20Directives.md)   
 [Conditional Compilation](../Topic/Conditional%20Compilation%20in%20Visual%20Basic.md)