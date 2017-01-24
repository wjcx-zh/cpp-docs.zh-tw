---
title: "無法實作與此簽章相符的成員 &#39;&lt;介面名稱&gt;.&lt;程序名稱&gt;&#39;，因為介面 &#39;&lt;介面名稱&gt;&#39; 包含多位具有此相同名稱與簽章的成員：&lt;簽章清單&gt; | Microsoft Docs"
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
  - "vbc30937"
  - "bc30937"
helpviewer_keywords: 
  - "BC30937"
ms.assetid: e917d85e-95e0-431a-9d09-39ce5d4fc894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法實作與此簽章相符的成員 &#39;&lt;介面名稱&gt;.&lt;程序名稱&gt;&#39;，因為介面 &#39;&lt;介面名稱&gt;&#39; 包含多位具有此相同名稱與簽章的成員：&lt;簽章清單&gt;
程序或屬性嘗試實作已在實作的介面中定義的程序或屬性，但編譯器發現多個版本之介面程序或屬性具有相同名稱和簽章。  
  
 這個錯誤可能發生在建構的泛型類型情況下，如下列基本架構宣告中所示。  
  
```  
Public Interface baseInterface(Of t) Sub doSomething(ByVal inputValue As String) Sub doSomething(ByVal inputValue As t) End Class Public Class implementingClass Implements baseInterface(Of String) Sub doSomething(ByVal inputValue As String) _ Implements baseInterface(Of String).doSomething End Sub End Class  
```  
  
 因為 `implementingClass` 實作 `baseInterface` 並提供 `String` 給其類型參數 `t`，所以就 `implementingClass` 而言，`baseInterface` 中的兩個版本 `doSomething` 會採取相同的簽章。 如此一來，編譯器無法判斷要實作哪一個版本。  
  
 **錯誤 ID︰**BC30937  
  
### 更正這個錯誤  
  
-   請變更您提供給基底類別的類型引數或引數，讓它不會導致成員程序或屬性有一或多個相同簽章。  
  
     \-或\-  
  
-   不要實作這個基底類別。 您無法以正在使用的類型引數集來實作它，因為您必須實作它的每一個成員。  
  
## 請參閱  
 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)