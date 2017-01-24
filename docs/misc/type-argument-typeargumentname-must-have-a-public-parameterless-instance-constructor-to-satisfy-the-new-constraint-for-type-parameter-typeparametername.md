---
title: "類型引數 &#39;&lt;類型引數名稱&gt;&#39; 必須擁有公用的無參數執行個體建構函式，才能滿足類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的 &#39;New&#39; 條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32083"
  - "BC32083"
helpviewer_keywords: 
  - "BC32083"
ms.assetid: 56bf25f1-375c-4b5d-9969-45eba8b3b66c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型引數 &#39;&lt;類型引數名稱&gt;&#39; 必須擁有公用的無參數執行個體建構函式，才能滿足類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的 &#39;New&#39; 條件約束
類型引數提供沒有可存取無參數建構函式的類型，給具有 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md) 條件約束的類型參數。  
  
 條件約束清單會對傳遞至類型參數的類型引數強制一些必要需求。 一項可能的需求是，類型引數必須公開建立程式碼可以存取的無參數建構函式。 為了指定這項需求，條件約束清單會包括 `New` 條件約束。  
  
 **錯誤 ID︰**BC32083  
  
### 更正這個錯誤  
  
1.  請確認泛型類型名稱和類型引數中的類型名稱拼字正確。  
  
2.  請為公開可存取無參數建構函式的類型引數選取一個類型。 除非您可以提供這種類型引數給這個類型參數，否則無法叫用這個特定的泛型類型。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [如何：使用泛型類別](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)