---
title: "類型引數無法套用至運算式 &#39;&lt;運算式&gt;&#39; | Microsoft Docs"
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
  - "bc32058"
  - "vbc32058"
helpviewer_keywords: 
  - "BC32058"
ms.assetid: c6b9b49c-6fb2-47b8-a8bb-464562d3adfd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型引數無法套用至運算式 &#39;&lt;運算式&gt;&#39;
使用將類型引數傳遞給匯入別名的 [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md) 子句，定義匯入別名。  
  
 類型引數用於泛型類型，而且只有類別、結構、介面、程序和委派才能是泛型。 命名空間和匯入別名可以是泛型。  
  
 **錯誤 ID：**BC32058  
  
### 更正這個錯誤  
  
-   請從匯入別名中移除 `Of` 子句和其類型引數。  
  
## 請參閱  
 [Imports Statement \(.NET Namespace and Type\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)   
 [References and the Imports Statement](../Topic/References%20and%20the%20Imports%20Statement%20\(Visual%20Basic\).md)   
 [NOTINBUILD：當多個變數擁有相同名稱時解析參考](http://msdn.microsoft.com/zh-tw/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)