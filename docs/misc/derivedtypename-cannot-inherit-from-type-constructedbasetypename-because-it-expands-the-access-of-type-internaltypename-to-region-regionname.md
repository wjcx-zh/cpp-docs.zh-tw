---
title: "&#39;&lt;衍生類型名稱&gt;&#39; 無法繼承自 &lt;類型&gt; &#39;&lt;建構基底類型名稱&gt;&#39;，因為它會將類型 &#39;&lt;內部類型名稱&gt;&#39; 的存取展開至 &lt;區域&gt; &#39;&lt;區域名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc30921"
  - "BC30921"
helpviewer_keywords: 
  - "BC30921"
ms.assetid: b0dd971a-80e2-4d37-925b-854d17411546
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;衍生類型名稱&gt;&#39; 無法繼承自 &lt;類型&gt; &#39;&lt;建構基底類型名稱&gt;&#39;，因為它會將類型 &#39;&lt;內部類型名稱&gt;&#39; 的存取展開至 &lt;區域&gt; &#39;&lt;區域名稱&gt;&#39;
衍生類別或介面嘗試使用內部類型作為基底類別或介面的類型引數，來展開內部類型的存取層級。  
  
 下列程式碼可能會產生此錯誤。  
  
```  
Public Class containingClass Public Class baseClass(Of t) End Class Friend Class derivedClass Inherits baseClass(Of internalStructure) End Class Private Structure internalStructure Dim firstMember As Integer End Structure End Class  
```  
  
 在 `containingClass` 外的程式碼不允許存取 `internalStructure`。 不過，`derivedClass` 可從相同組件中的任何程式碼進行存取。 因此，如果使用 `internalStructure` 作為類型引數，`derivedClass` 就無法繼承 `baseClass`，因為這樣做可能會公開整個定義程式碼區域的 `internalStructure`。  
  
 **錯誤 ID︰**BC30921  
  
### 更正這個錯誤  
  
-   調整類別或介面的存取層級，讓衍生類型不會展開內部類型的存取層級。  
  
     \-或\-  
  
-   如果您無法調整存取層級，則請勿在建構基底類別或介面時使用內部類型作為類型引數。  
  
## 請參閱  
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)