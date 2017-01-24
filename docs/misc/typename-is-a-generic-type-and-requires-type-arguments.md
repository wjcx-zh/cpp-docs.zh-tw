---
title: "&#39;&lt;類型名稱&gt;&#39; 是泛型類型而且需要類型引數。 | Microsoft Docs"
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
  - "BC32076"
  - "vbc32076"
helpviewer_keywords: 
  - "BC32076"
ms.assetid: 57f63727-c544-4012-8f03-5d77fbdd1135
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類型名稱&gt;&#39; 是泛型類型而且需要類型引數。
宣告變數、程序參數或函式傳回是為取得泛型類別或結構的類型，但宣告並不提供任何類型引數。  
  
 本質上，每個泛型類別和結構都定義了至少一個類型參數。 當您使用泛型類型宣告已建構的類別或結構時，您必須為泛型類型定義的所有類型參數提供類型引數。  
  
 **錯誤識別碼：**BC32076  
  
### 更正這個錯誤  
  
-   將類型清單加入宣告內，以括弧括住且開頭為 `Of` 關鍵字。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)