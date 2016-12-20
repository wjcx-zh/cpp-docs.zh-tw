---
title: "&#39;&lt;項目名稱&gt;&#39; 參考專案 &#39;&lt;專案名稱&gt;&#39; 中的 &#39;&lt;類型名稱&gt;&#39; 類型，但在專案 &#39;&lt;專案名稱&gt;&#39; 中找不到類型 &#39;&lt;類型名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc30960"
  - "bc30960"
helpviewer_keywords: 
  - "BC30960"
ms.assetid: 4ed4bff5-c670-46f6-8360-7287444d50e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;項目名稱&gt;&#39; 參考專案 &#39;&lt;專案名稱&gt;&#39; 中的 &#39;&lt;類型名稱&gt;&#39; 類型，但在專案 &#39;&lt;專案名稱&gt;&#39; 中找不到類型 &#39;&lt;類型名稱&gt;&#39;
運算式存取另一個專案中參考的類別、結構、模組或介面，但該專案未包含指定的類型。  
  
 您的專案對相同方案中的另一個專案進行間接參考時，就會發生此錯誤。 一般而言，您的專案會參考參考另一個專案的組件。 如果組件存取另一個專案中的指定類型，則會建立對類型的間接參考。 不過，如果類型不在另一個專案中，就會產生此錯誤。  
  
 **錯誤 ID︰**BC30960  
  
### 更正這個錯誤  
  
-   如果所指出類型不再於任何地方定義，那麼請移除或取代嘗試存取它的陳述式。 您可能也需要在提供對所指出類型之間接參考的組件中進行相同變更。  
  
-   如果所指出類型定義於某處，則請直接參考定義它的專案或組件。  
  
## 請參閱  
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB：管理參考](http://msdn.microsoft.com/zh-tw/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)