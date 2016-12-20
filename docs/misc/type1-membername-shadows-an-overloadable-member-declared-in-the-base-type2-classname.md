---
title: "&lt;類型1&gt; &#39;&lt;成員名稱&gt;&#39; 遮蔽基底 &lt;類型2&gt; &#39;&lt;類別名稱&gt;&#39; 中宣告的可多載成員 | Microsoft Docs"
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
  - "bc40003"
  - "vbc40003"
helpviewer_keywords: 
  - "BC40003"
ms.assetid: 1e0d2061-0ad9-4915-b946-d55cb5d5ee80
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;類型1&gt; &#39;&lt;成員名稱&gt;&#39; 遮蔽基底 &lt;類型2&gt; &#39;&lt;類別名稱&gt;&#39; 中宣告的可多載成員
\<類型1\> '\<成員名稱\>' 遮蔽基底 \<類型2\> '\<類別名稱\>' 中宣告的可多載成員。 如果您要多載基底方法，必須將這個方法宣告為 'Overloads'。  
  
 衍生類別定義 `Function` 或 `Sub` 程序或 `Property` 所使用的名稱，與基底類別中所定義之程序或屬性的名稱相同。 由於程序和屬性是可多載成員，因此衍生類別可以多載或遮蔽基底類別成員。 但是，衍生類別程式碼未在宣告中指定 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 或 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)。 如果沒有其中一個關鍵字，編譯器會假設 `Shadows`。  
  
 最佳程式設計做法是指定 `Overloads` 或 `Shadows`。 如此可讓您的程式碼更容易閱讀及了解。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40003  
  
### 更正這個錯誤  
  
-   如果您要多載基底類別方法或屬性，請在宣告中包含 `Overloads` 關鍵字。  
  
-   如果您要遮蔽基底類別方法或屬性，請包含 `Shadows` 關鍵字，而不是 `Overloads`。  
  
-   如果您不想要多載或遮蔽基底類別成員，請變更衍生類別成員的名稱。  
  
## 請參閱  
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)   
 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md)   
 [Sub Statement](../Topic/Sub%20Statement%20\(Visual%20Basic\).md)   
 [Property Statement](../Topic/Property%20Statement.md)