---
title: "&#39;&lt;衍生類型名稱&gt;&#39; 無法繼承自 &lt;t類型&gt; &#39;&lt;建構的基底類型名稱&gt;&#39;，因為它會在組件之外展開類型 &#39;&lt;內部類型名稱&gt;&#39; 的存取 | Microsoft Docs"
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
  - "BC30922"
  - "vbc30922"
helpviewer_keywords: 
  - "BC30922"
ms.assetid: 81909654-7e67-4b89-81a3-25ae57f678f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;衍生類型名稱&gt;&#39; 無法繼承自 &lt;t類型&gt; &#39;&lt;建構的基底類型名稱&gt;&#39;，因為它會在組件之外展開類型 &#39;&lt;內部類型名稱&gt;&#39; 的存取
衍生的類別或介面嘗試使用受限類型作為基底類別或介面的類型引數，來展開受限類型的存取層級。  
  
 下列程式碼可能會產生此錯誤。  
  
```  
Public Class baseClass(Of t)  
End Class  
Public Class derivedClass  
    Inherits baseClass(Of restrictedStructure)  
End Class  
Friend Structure restrictedStructure  
    Dim firstMember As Integer  
End Structure  
```  
  
 在組件外的程式碼不允許存取 `restrictedStructure`。 不過，可以從任何可參考 `derivedClass` 的程式碼存取它。 因此，`derivedClass` 無法繼承 `baseClass`，如果它使用 `restrictedStructure` 作為類型引數的話，因為那可能將 `restrictedStructure` 公開給任何組件中的程式碼。  
  
 **錯誤 ID︰**BC30922  
  
### 更正這個錯誤  
  
-   請調整類別或介面的存取層級，讓衍生類型不會展開受限類型的存取層級。  
  
     \-或\-  
  
-   如果您不能調整存取層級，請勿在建構基底類別或介面時使用受限類型作為類型引數。  
  
## 請參閱  
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)