---
title: "無法繼承介面 &#39;&lt;介面名稱1&gt;&#39;，因為它可能與某些類型引數的介面 &#39;&lt;介面名稱2&gt;&#39; 相同。 | Microsoft Docs"
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
  - "vbc32120"
  - "bc32120"
helpviewer_keywords: 
  - "BC32120"
ms.assetid: c91f84a1-e61d-4b5f-8028-221e64ac044c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法繼承介面 &#39;&lt;介面名稱1&gt;&#39;，因為它可能與某些類型引數的介面 &#39;&lt;介面名稱2&gt;&#39; 相同。
泛型介面多次繼承自另一個泛型介面，而且兩個繼承的類型引數之特定值可能發生衝突。  
  
 下列陳述式可能會產生此錯誤。  
  
 `Public Interface interfaceA(Of u)`  
  
 `End Interface`  
  
 `Public Interface derivedInterface(Of t1, t2)`  
  
 `Inherits interfaceA(Of t1), interfaceA(Of t2)`  
  
 `End Interface`  
  
 如果建構或實作 `derivedInterface` 時針對 `t1` 和 `t2` 提供相同的類型，其一定會繼承含相同類型引數之 `interfaceA` 的兩個版本。 這樣會造成無法確定存取哪一個版本的情況。  
  
 **錯誤 ID︰**BC32120  
  
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