---
title: "具有前置字元的命名空間宣告在 XML 常值中不能有空值 | Microsoft Docs"
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
  - "bc31184"
  - "vbc31184"
helpviewer_keywords: 
  - "BC31184"
ms.assetid: dde656b4-df3b-4a2e-8871-4e14832ca778
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 具有前置字元的命名空間宣告在 XML 常值中不能有空值
XML 常值中的 XML 命名空間宣告不包含命名空間值。 例如，下列程式碼會造成這個錯誤：  
  
```vb#  
Dim book = <book xmlns:ns=""/>  
```  
  
 **錯誤 ID︰**BC31184  
  
### 更正這個錯誤  
  
-   在 XML 命名空間宣告中包含有效的命名空間，或從 XML 常值中移除 XML 命名空間宣告。  
  
     或者，您可以使用 `Imports` 陳述式來識別空命名空間的命名空間前置字元。 例如:  
  
    ```vb#  
    Imports <xmlns:ns="">  
    ```  
  
## 請參閱  
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)   
 [Imports Statement \(XML Namespace\)](../Topic/Imports%20Statement%20\(XML%20Namespace\).md)