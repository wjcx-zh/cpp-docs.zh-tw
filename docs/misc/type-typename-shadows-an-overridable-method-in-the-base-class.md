---
title: "&lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 遮蔽了基底類別中可覆寫的方法 | Microsoft Docs"
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
  - "vbc40005"
  - "bc40005"
helpviewer_keywords: 
  - "BC40005"
ms.assetid: 1dadda7f-1d26-4ae8-a668-9f69d55ceb50
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 遮蔽了基底類別中可覆寫的方法
\<類型\> '\<類型名稱\>' 遮蔽了基底類別中可覆寫的方法。 如果您要覆寫基底方法，必須將這個方法宣告為 'Overrides'。  
  
 宣告程式設計項目所使用的名稱，與基底類別中所定義之可覆寫程序或屬性的名稱相同。 在這種情況下，這個類別中的項目應該會遮蔽基底類別項目。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40005  
  
### 更正這個錯誤  
  
-   如果您想要覆寫基底程序，請將 `Overrides` 關鍵字加入宣告中。  
  
-   如果您想要遮蔽基底程序，請將 `Shadows` 關鍵字加入宣告中。  
  
-   如果您不想要覆寫或遮蔽，請變更所宣告之項目的名稱。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)