---
title: "條件約束 &#39;&lt;條件約束1&gt;&#39; 與從類型參數條件約束 &#39;&lt;類型參數1&gt;&#39; 取得的間接條件約束 &#39;&lt;條件約束2&gt;&#39;，互相衝突 | Microsoft Docs"
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
  - "bc32110"
  - "vbc32110"
helpviewer_keywords: 
  - "BC32110"
ms.assetid: e799214d-23b4-4a3f-b61a-0b9d3387ead3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 條件約束 &#39;&lt;條件約束1&gt;&#39; 與從類型參數條件約束 &#39;&lt;類型參數1&gt;&#39; 取得的間接條件約束 &#39;&lt;條件約束2&gt;&#39;，互相衝突
宣告的泛型類型因直接和間接條件約束組合而具有衝突的條件約束。  
  
 下列陳述式可能會產生這個錯誤。  
  
 `Public Class testClass(Of t1 As {Structure, t2}, t2 As Class)`  
  
 直接條件約束 `Structure` 和間接條件約束 `Class` 導致類型參數 `t1` 的衝突，因為 `Structure` 條件約束需要對應的類型引數是實值類型，而 `Class` 需要它是參考類型。  
  
 **錯誤 ID︰**BC32110  
  
### 更正這個錯誤  
  
-   請變更類型參數條件約束，以避免衝突的條件約束。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [結構 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [類別 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)