---
title: "無法實作 &#39;&lt;介面名稱1&gt;.&lt;成員名稱&gt;&#39;，因為實作這個項目可能會和某些類型引數的 &#39;&lt;介面名稱2&gt;.&lt;成員名稱&gt;&#39; 實作發生衝突。 | Microsoft Docs"
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
  - "bc32125"
  - "vbc32125"
helpviewer_keywords: 
  - "BC32125"
ms.assetid: 74321d27-4ff8-440c-b5de-d67e98fff274
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法實作 &#39;&lt;介面名稱1&gt;.&lt;成員名稱&gt;&#39;，因為實作這個項目可能會和某些類型引數的 &#39;&lt;介面名稱2&gt;.&lt;成員名稱&gt;&#39; 實作發生衝突。
類別實作多個泛型介面，其中一個繼承另一個，還有兩個介面成員的實作可能和類型引數的特定值發生衝突。  
  
 下列陳述式可能會產生此錯誤。  
  
```  
Public Interface iFace1(Of t) Sub testSub() End Interface Public Interface iFace2(Of u) Inherits iFace1(Of u) End Interface Public Class testClass(Of y, z) Implements iFace1(Of y), iFace2(Of z) Public Sub testSuby() Implements iFace1(Of y).testSub End Sub Public Sub testSubz() Implements iFace1(Of z).testSub End Sub End Class  
```  
  
 因為 `iFace2` 使用自己的類型參數 \(`u`\) 繼承了 `iFace1`，所以，如果相同的類型引數傳遞到 `y` 和 `z`，`testClass` 就會實作具有相同特徵標記的兩個版本的 `iFace1.testSub`。 這樣會造成不知該存取哪一個版本的情況。  
  
 **錯誤識別碼：**BC32125  
  
### 更正這個錯誤  
  
-   請變更介面的繼承結構，讓 `iFace1` 不能和兩個不同的類型引數一起實作。  
  
     \-或\-  
  
-   從 `Implements` 陳述式移除其中一個造成實作衝突的介面。  
  
## 請參閱  
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)