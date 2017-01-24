---
title: "無法繼承介面 &#39;&lt;介面名稱1&gt;&#39;，因為它可能和介面 &#39;&lt;介面名稱2&gt;&#39; 相同，後者來自繼承某些類型引數的介面 &#39;&lt;介面3&gt;&#39; | Microsoft Docs"
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
  - "bc32123"
  - "vbc32123"
helpviewer_keywords: 
  - "BC32123"
ms.assetid: 2b8fa1f0-3d43-45c6-99d0-328151479b43
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法繼承介面 &#39;&lt;介面名稱1&gt;&#39;，因為它可能和介面 &#39;&lt;介面名稱2&gt;&#39; 相同，後者來自繼承某些類型引數的介面 &#39;&lt;介面3&gt;&#39;
泛型介面繼承自兩個以上的泛型介面，而且兩個繼承的類型引數之特定值可能發生衝突。  
  
 下列陳述式可能會產生此錯誤。  
  
```  
Public Interface interfaceA(Of u) End Interface Public Interface interfaceX(Of v) Inherits interfaceA(Of v) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceA(Of t1), interfaceX(Of t2) End Interface  
```  
  
 如果建構或實作 `derivedInterface` 時針對 `t1` 和 `t2` 提供相同的類型，其一定會繼承含相同類型引數之 `interfaceA` 的兩個版本。 這樣會造成無法確定存取哪一個版本的情況。  
  
 **錯誤 ID：**BC32123  
  
### 更正這個錯誤  
  
-   變更其中一個提供給衍生介面的類型引數，使其沒有衝突。  
  
     \-或\-  
  
-   從 `Inherits` 陳述式中，移除其中一個可能導致繼承或實作衝突的介面。  
  
## 請參閱  
 [不在組建中：介面概觀](http://msdn.microsoft.com/zh-tw/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)   
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)