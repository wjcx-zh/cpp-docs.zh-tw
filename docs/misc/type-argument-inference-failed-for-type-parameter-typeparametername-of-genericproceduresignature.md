---
title: "&#39;&lt;泛型程序簽章&gt;&#39; 之類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的類型引數推斷失敗 | Microsoft Docs"
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
  - "vbc32051"
  - "bc32051"
helpviewer_keywords: 
  - "BC32051"
ms.assetid: a9c2a0ce-e225-4549-bfd8-d42df5d16bfd
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;泛型程序簽章&gt;&#39; 之類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的類型引數推斷失敗
'\<泛型程序簽章\>' 之類型參數 '\<類型參數名稱\>' 的類型引數推斷失敗。 無法從傳遞給參數 '\<參數名稱\>' 的引數推斷類型引數。  
  
 泛型程序是在未提供任何類型引數的情況下呼叫，而且編譯器無法推斷要傳遞給其中一個參數的類型。  
  
 通常，當您呼叫泛型程序時，會針對泛型程序所定義的每個類型參數提供類型引數。 如果您未提供任何類型引數，則編譯器會嘗試推斷要傳遞給類型參數的類型。 如果呼叫的內容提供類型參數的衝突資料類型資訊，則類型推斷會失敗。  
  
 下列程式碼可能會產生此錯誤。  
  
```  
Public Sub doSomething(Of t)(ByVal arg1 As t(), ByVal arg2 As t) End Sub Call doSomething(6, 42)  
```  
  
 在上述範例中，編譯器會根據傳遞給 `arg2` 的值 42 來推斷 `t` 的類型 `Integer`。 不過，該推斷需要 `arg1` 為類型 `Integer()` \(即 `Integer` 的陣列\)，而且傳遞給 `arg1` 的值 6 不符合該類型。  
  
 **錯誤 ID︰**BC32051  
  
### 更正這個錯誤  
  
-   請將類型引數提供給泛型程序，這樣編譯器就不需要推斷它們。  
  
-   請提供類型符合類型引數之類型的一般引數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)