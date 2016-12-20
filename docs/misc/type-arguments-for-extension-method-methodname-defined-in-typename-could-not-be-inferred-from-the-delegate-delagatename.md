---
title: "無法從委派 &#39;&lt;委派名稱&gt;&#39; 推斷在 &#39;&lt;類型名稱&gt;&#39; 中定義之擴充方法 &#39;&lt;方法名稱&gt;&#39; 的類型引數 | Microsoft Docs"
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
  - "bc36581"
  - "vbc36581"
helpviewer_keywords: 
  - "BC36581"
ms.assetid: 2bb9ca8d-7293-40e9-9285-e20b8254b3af
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從委派 &#39;&lt;委派名稱&gt;&#39; 推斷在 &#39;&lt;類型名稱&gt;&#39; 中定義之擴充方法 &#39;&lt;方法名稱&gt;&#39; 的類型引數
指派陳述式使用 `AddressOf` 將泛型擴充方法的位址指派給委派，但未將任何類型引數提供給擴充方法。  
  
 通常，當您叫用泛型方法時，會針對泛型方法所定義的每個類型參數提供類型引數。 如果您未提供任何類型引數，編譯器會嘗試推斷要傳遞給類型參數的類型。 如果內容未提供足夠的資訊讓編譯器推斷類型，則會產生錯誤。  
  
 **錯誤 ID：**BC36581  
  
### 更正這個錯誤  
  
-   在 `AddressOf` 運算式中指定擴充方法的類型引數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)