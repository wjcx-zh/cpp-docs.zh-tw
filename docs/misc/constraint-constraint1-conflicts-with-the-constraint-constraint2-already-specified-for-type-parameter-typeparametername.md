---
title: "條件約束 &#39;&lt;條件約束1&gt;&#39; 和為類型參數 &#39;&lt;類型參數名稱&gt;&#39; 指定的條件約束 &#39;&lt;條件約束2&gt;&#39; 發生衝突 | Microsoft Docs"
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
  - "vbc32119"
  - "bc32119"
helpviewer_keywords: 
  - "BC32119"
ms.assetid: 30e6778d-5c2b-4f2d-a136-4e66fa9fbe4d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 條件約束 &#39;&lt;條件約束1&gt;&#39; 和為類型參數 &#39;&lt;類型參數名稱&gt;&#39; 指定的條件約束 &#39;&lt;條件約束2&gt;&#39; 發生衝突
泛型類型使用類型參數上相衝突的條件約束宣告。  
  
 下列陳述式可能會產生這個錯誤。  
  
 `Public Class testClass(Of t As {Structure, Class })`  
  
 類型參數 `t` 的條件約束 `Structure` 和 `Class` 會導致衝突，因為 `Structure` 條件約束需要對應的類型參數是實值類型，而 `Class` 需要它是參考類型。  
  
 **錯誤 ID：**BC32119  
  
### 更正這個錯誤  
  
-   請變更類型參數條件約束，以避免衝突。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [結構 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [類別 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)