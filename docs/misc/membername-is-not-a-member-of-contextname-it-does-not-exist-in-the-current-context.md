---
title: "&#39;&lt;成員名稱&gt;&#39; 不是 &#39;&lt;內容名稱&gt;&#39; 的成員，它不存在於目前的內容中 | Microsoft Docs"
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
  - "vbc36557"
  - "bc36557"
helpviewer_keywords: 
  - "BC36557"
ms.assetid: d8671f1c-d545-44da-89b3-7d892e01e8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;成員名稱&gt;&#39; 不是 &#39;&lt;內容名稱&gt;&#39; 的成員，它不存在於目前的內容中
不存在的成員名稱已被指派至匿名類型宣告的屬性。 在下列範例中，`.Prop1` 和 `.Prop2` 是匿名類型的屬性。 嘗試將 `.Prop3` 指派至 `.Prop2` 造成錯誤。  
  
```vb#  
' Not valid.  
Dim anon1 = New With {.Prop1 = 27, .Prop2 = .Prop3}  
  
' The assignment is valid if the assigned property has been declared   
' and initialized.  
Dim anon2 = New With {.Prop1 = 27, .Prop2 = .Prop1}  
```  
  
 **錯誤 ID︰**BC36657  
  
### 更正這個錯誤  
  
-   請檢查您的程式碼，判斷您想要指派的項目。 變數名稱可能拼錯，或者如果它是另一個物件的屬性，則可能需要限定性條件。  
  
## 請參閱  
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)