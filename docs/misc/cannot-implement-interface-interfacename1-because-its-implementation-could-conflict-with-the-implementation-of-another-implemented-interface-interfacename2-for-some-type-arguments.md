---
title: "無法實作介面 &#39;&lt;介面名稱1&gt;&#39;，因為它的實作可能與某些類型引數的另一個實作介面 &#39;&lt;介面名稱2&gt;&#39; 之實作互相衝突。 | Microsoft Docs"
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
  - "BC32072"
  - "vbc32072"
helpviewer_keywords: 
  - "BC32072"
ms.assetid: af1cc688-c8cf-4cb2-a8a9-310f5139fe7b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法實作介面 &#39;&lt;介面名稱1&gt;&#39;，因為它的實作可能與某些類型引數的另一個實作介面 &#39;&lt;介面名稱2&gt;&#39; 之實作互相衝突。
類別宣告包含指定兩個或多個介面的 `Implements` 陳述式，但至少有一個介面是泛型，且有兩個實作因為特定的類型引數值而發生衝突。  
  
 下列陳述式可能會產生此錯誤。  
  
```  
Public Interface iFace1 Sub testSub(ByVal arg As String) End Interface Public Interface iFace2(Of t) Sub testSub(ByVal arg As t) End Interface Public Class testClass Implements iFace1, iFace2(Of String) End Class  
```  
  
 因為 `iFace2` 使用 `String` 建構，所以 `testClass` 必須實作具相同特徵標記的兩個版本 `testSub`。 這樣會造成無法確定存取哪一個版本的情況。  
  
 **錯誤 ID：**BC32072  
  
### 更正這個錯誤  
  
-   變更提供給泛型介面的類型引數，使其不發生衝突。  
  
     \-或\-  
  
-   從 `Implements` 陳述式移除其中一個造成實作衝突的介面。  
  
## 請參閱  
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)