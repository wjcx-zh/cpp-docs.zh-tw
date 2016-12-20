---
title: "Option Strict 為 On 時，不可將 ByRef 參數 &#39;&lt;參數名稱&gt;&#39; 的值複製回相對應的引數，而將類型 &#39;&lt;類型名稱1&gt;&#39; 縮減為類型 &#39;&lt;類型名稱2&gt;&#39; | Microsoft Docs"
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
  - "bc32029"
  - "vbc32029"
helpviewer_keywords: 
  - "BC32029"
ms.assetid: fc9ae5d2-b506-47cf-a50c-116fda5ed206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict 為 On 時，不可將 ByRef 參數 &#39;&lt;參數名稱&gt;&#39; 的值複製回相對應的引數，而將類型 &#39;&lt;類型名稱1&gt;&#39; 縮減為類型 &#39;&lt;類型名稱2&gt;&#39;
程序呼叫提供了 `ByRef` 引數，其資料類型可擴展成引數的宣告類型，而且 `Option Strict` 為 `On`。 將此引數傳遞至程序時允許擴展轉換，但是當程序修改呼叫程式碼中的變數引數內容時，會縮小反向轉換。`Option Strict On` 不允許縮小轉換。  
  
 **錯誤 ID︰**BC32029  
  
### 更正這個錯誤  
  
-   為程序呼叫中的每個 `ByRef` 引數提供與宣告類型相同的資料類型，或開啟 `Option Strict Off`。  
  
## 請參閱  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)