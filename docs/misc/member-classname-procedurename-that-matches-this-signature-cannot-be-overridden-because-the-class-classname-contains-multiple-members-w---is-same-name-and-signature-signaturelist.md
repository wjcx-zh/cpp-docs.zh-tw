---
title: "無法覆寫與此簽章相符的成員 &#39;&lt;類別名稱&gt;.&lt;程序名稱&gt;&#39;，因為類別 &#39;&lt;類別名稱&gt;&#39; 包含多位具有此相同名稱與簽章的成員：&lt;簽章清單&gt; | Microsoft Docs"
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
  - "bc30935"
  - "vbc30935"
helpviewer_keywords: 
  - "BC30935"
ms.assetid: 1165b630-668d-417d-9e18-9b8ffe7f6980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法覆寫與此簽章相符的成員 &#39;&lt;類別名稱&gt;.&lt;程序名稱&gt;&#39;，因為類別 &#39;&lt;類別名稱&gt;&#39; 包含多位具有此相同名稱與簽章的成員：&lt;簽章清單&gt;
程序或屬性嘗試覆寫繼承的程序或屬性，但編譯器發現多個版本的基底程序或屬性具有相同名稱和簽章。  
  
 這個錯誤可能發生在建構的泛型類型情況下，如下列基本架構宣告中所示。  
  
```  
Public Class baseClass(Of t) Public Overridable Sub doSomething(ByVal inputValue As String) End Sub Public Overridable Sub doSomething(ByVal inputValue As t) End Sub End Class Public Class derivedClass Inherits baseClass(Of String) Overrides Sub doSomething(ByVal inputValue As String) End Sub End Class  
```  
  
 因為 `derivedClass` 繼承 `baseClass` 並提供 `String` 給其類型參數 `t`，所以就 `derivedClass` 而言，`baseClass` 中的兩個 `doSomething` 版本會採取相同的簽章。 如此一來，編譯器無法判斷要覆寫的版本。  
  
 **錯誤 ID︰**BC30935  
  
### 更正這個錯誤  
  
-   請變更您提供給基底類別的類型引數或引數，讓它不會導致成員程序或屬性有一或多個相同簽章。  
  
     \-或\-  
  
-   如果您需要繼承具有所使用類型引數集合的基底類別，則請不要覆寫這個錯誤訊息中所提到的程序或屬性。  
  
## 請參閱  
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)