---
title: "必須是類型或 &#39;With&#39; | Microsoft Docs"
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
  - "vbc30988"
  - "bc30988"
helpviewer_keywords: 
  - "BC30988"
ms.assetid: ab9c0cee-9fe4-4764-a3c2-aec16e709d4c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是類型或 &#39;With&#39;
當您宣告類別的執行個體時，`New` 關鍵字後面必須接著類型名稱或 `With`。 例如，下列陳述式每個都宣告 `client` 為 `Customer` 類別的執行個體。`New` 後面是類型名稱 `Customer`。  
  
```  
' Dim client As New Customer()  
' The next declaration uses an object initializer.  
Dim client As New Customer() With {.Name = "Litware, Inc."}  
```  
  
 開頭為 [!INCLUDE[vb_orcas_long](../misc/includes/vb_orcas_long_md.md)]，您可以宣告物件是匿名類型的執行個體，這樣就不用指定資料類型。 在匿名類型宣告中，關鍵字 `With` 跟隨在 `New` 的後面。  
  
```  
Dim person = New With {.Name ="Mike Nash", .Age = 27}  
```  
  
 **錯誤 ID：**BC30988  
  
### 更正這個錯誤  
  
-   變更宣告，讓 `With` 或類型名稱跟隨在 `New` 的後面。  
  
## 請參閱  
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [NotInBuild：Visual Basic 中的 Declaration 陳述式](http://msdn.microsoft.com/zh-tw/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)