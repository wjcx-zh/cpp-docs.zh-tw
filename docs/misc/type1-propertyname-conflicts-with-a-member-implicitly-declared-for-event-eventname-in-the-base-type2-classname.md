---
title: "&lt;類型1&gt; &#39;&lt;屬性名稱&gt;&#39; 與針對基底 &lt;類型2&gt; &#39;&lt;類別名稱&gt;&#39; 中事件 &#39;&lt;事件名稱&gt;&#39; 進行隱含宣告的成員互相衝突 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40014"
  - "bc40014"
helpviewer_keywords: 
  - "BC40014"
ms.assetid: 100534b9-d533-4e94-a2a7-0ed26426965b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;類型1&gt; &#39;&lt;屬性名稱&gt;&#39; 與針對基底 &lt;類型2&gt; &#39;&lt;類別名稱&gt;&#39; 中事件 &#39;&lt;事件名稱&gt;&#39; 進行隱含宣告的成員互相衝突
所宣告的屬性與隱含成員同名，而隱含成員是從基底類別中的事件所形成。 例如，如果基底類別定義名為 `Event1` 的事件，則編譯器會產生隱含程序 `add_Event1` 和 `remove_Event1`。 如果這個類別中的屬性具有上述其中一個名稱，則應該會遮蔽基底類別成員。  
  
 這個訊息是一個警告。 預設會假設為 `Shadows`。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40014  
  
### 更正這個錯誤  
  
1.  若要隱藏基底類別成員，請將 `Shadows` 關鍵字加入屬性宣告中。  
  
2.  如果您不想要隱藏基底類別成員，請變更屬性名稱。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Event Statement](../Topic/Event%20Statement.md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)