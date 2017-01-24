---
title: "基底類別 &#39;&lt;基底類別名稱&gt;&#39; 已實作 &#39;implements &lt;衍生介面名稱&gt;&#39; 中的 &#39;&lt;基底介面名稱&gt;.&lt;成員名稱&gt;&#39;。 假設重新實作 &lt;類型&gt; | Microsoft Docs"
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
  - "bc42014"
  - "vbc42014"
helpviewer_keywords: 
  - "BC42014"
ms.assetid: 95fff622-5d54-4ec8-90f0-477de1d58687
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 基底類別 &#39;&lt;基底類別名稱&gt;&#39; 已實作 &#39;implements &lt;衍生介面名稱&gt;&#39; 中的 &#39;&lt;基底介面名稱&gt;.&lt;成員名稱&gt;&#39;。 假設重新實作 &lt;類型&gt;
衍生類別中的屬性、程序或事件透過指定已在基底類別的基底介面上實作的衍生介面成員，來使用 `Implements` 子句。  
  
 所實作的成員是由基底介面所定義，並且透過衍生介面予以繼承。 基底類別會直接實作基底介面。 衍生類別會實作衍生介面，而且很容易漏掉基底類別已實作成員的事實。  
  
 衍生類別可以重新實作透過其基底類別所實作的介面成員。 這與覆寫基底類別實作不同。 如需詳細資訊，請參閱[Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42014  
  
### 更正這個錯誤  
  
-   如果您要重新實作介面成員，則不需要採取任何動作。 除非您使用 [MyBase \- delete](http://msdn.microsoft.com/zh-tw/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) 關鍵字存取基底類別實作，否則衍生類別中的程式碼會存取重新實作的成員。  
  
-   如果您不要重新實作介面成員，請從屬性、程序或事件宣告中移除 `Implements` 子句。  
  
## 請參閱  
 [Interfaces](../Topic/Interfaces%20\(Visual%20Basic\).md)   
 [不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)