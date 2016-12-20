---
title: "事件 &#39;&lt;事件名稱&gt;&#39; 隱含宣告 &#39;&lt;成員名稱&gt;&#39;，它與基底 &lt;類型&gt; &#39;&lt;類別名稱&gt;&#39; 中的成員產生衝突，所以事件應該宣告為 &#39;Shadows&#39; | Microsoft Docs"
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
  - "bc40012"
  - "vbc40012"
helpviewer_keywords: 
  - "BC40012"
ms.assetid: 5f14e8bd-a227-4115-af99-cd2b6fe4dc0e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 事件 &#39;&lt;事件名稱&gt;&#39; 隱含宣告 &#39;&lt;成員名稱&gt;&#39;，它與基底 &lt;類型&gt; &#39;&lt;類別名稱&gt;&#39; 中的成員產生衝突，所以事件應該宣告為 &#39;Shadows&#39;
宣告事件所使用的名稱，可以搭配基底類別成員的相同名稱來形成隱含成員。 例如，如果您宣告名為 `Event1` 的事件，編譯器會產生隱含程序 `add_Event1` 和 `remove_Event1`。 如果基底類別中有任何成員具有上述其中一個名稱，則這個類別中的事件應該遮蔽此基底類別成員。  
  
 這個訊息是一個警告。 預設會假設為 `Shadows`。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40012  
  
### 更正這個錯誤  
  
1.  若要隱藏基底類別成員，請將 `Shadows` 關鍵字加入事件宣告中。  
  
2.  如果您不想要隱藏基底類別成員，請變更事件的名稱。  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)