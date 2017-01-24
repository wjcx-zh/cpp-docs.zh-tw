---
title: "方法 &#39;&lt;方法名稱&gt;&#39; 有連結需求，但是會覆寫或實作沒有連結需求的方法。 可能會有安全性漏洞： | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42200"
  - "vbc42200"
helpviewer_keywords: 
  - "BC42200"
ms.assetid: c79d672e-638c-4d87-9b93-edf12ce84a52
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 &#39;&lt;方法名稱&gt;&#39; 有連結需求，但是會覆寫或實作沒有連結需求的方法。 可能會有安全性漏洞：
已將安全性連結需求動作加入方法中。 不過，這個方法會覆寫或實作沒有連結需求的方法。 因此，即使權限不足，還是可以呼叫覆寫或實作的方法，這樣可能會造成安全性問題。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42200  
  
### 更正這個錯誤  
  
-   將連結需求加入覆寫及\/或實作的方法中。  
  
## 請參閱  
 [Link Demands](../Topic/Link%20Demands.md)   
 [Demand 與LinkDemand 的比較](http://msdn.microsoft.com/zh-tw/1ab877f2-70f4-4e0d-8116-943999dfe8f5)   
 [安全性最佳化](http://msdn.microsoft.com/zh-tw/cf255069-d85d-4de3-914a-e4625215a7c0)