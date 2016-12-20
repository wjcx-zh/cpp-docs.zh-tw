---
title: "匿名類型成員屬性 &#39;&lt;屬性名稱&gt;&#39; 無法用來推斷另一個成員屬性的類型，因為尚未建立類型 &#39;&lt;屬性名稱&gt;&#39;。 | Microsoft Docs"
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
  - "vbc36559"
  - "bc36559"
helpviewer_keywords: 
  - "BC36559"
ms.assetid: 58ab8d35-9d85-4aca-8b4e-f232d7e4af61
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名類型成員屬性 &#39;&lt;屬性名稱&gt;&#39; 無法用來推斷另一個成員屬性的類型，因為尚未建立類型 &#39;&lt;屬性名稱&gt;&#39;。
在匿名類型屬性的類型建立之前，它不能用以建立另一個屬性的類型。 例如，`.IDName = .LastName` 在下列宣告中是無效的，因為 `.LastName` 尚未初始化。  
  
```  
' Not valid.   
' Dim anon1 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}   
```  
  
 **錯誤識別碼：**BC36559  
  
### 更正這個錯誤  
  
-   請先建立屬性類型，再使用它初始化其他屬性。  
  
    ```  
    Dim anon2 = New With {Key .LastName = "Jones", Key .IDName = .LastName}  
    ```  
  
## 請參閱  
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)