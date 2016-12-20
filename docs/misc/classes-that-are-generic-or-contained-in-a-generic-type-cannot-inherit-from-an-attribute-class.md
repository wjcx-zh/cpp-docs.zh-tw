---
title: "泛型類別或包含在泛型類型中的類別不可以繼承自屬性類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32074"
  - "BC32074"
helpviewer_keywords: 
  - "BC32074"
ms.assetid: 3552ac98-d86a-4962-9d51-b9a8acc38ea1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 泛型類別或包含在泛型類型中的類別不可以繼承自屬性類別
泛型類型內的泛型或巢狀類別指定它繼承自屬性類別。  
  
 Visual Basic 和 .NET Framework 目前不支援任何屬性和泛型類型組合。 這表示會套用下列限制：  
  
-   屬性不能是泛型類型或在泛型類型內進行宣告。  
  
-   屬性不可以繼承自泛型類別，泛型類別也不可以繼承自屬性。  
  
-   當您套用屬性時，不可以提供下列任何引數：  
  
    -   泛型類型、  
  
    -   建構自泛型類型的類型、  
  
    -   包含類型的類型參數，或  
  
    -   建構自包含類型之類型參數的類型。  
  
 **錯誤 ID︰**BC32074  
  
### 更正這個錯誤  
  
-   請將基底類別變更為屬性類別以外的值，或整個移除 `Inherits` 陳述式。  
  
## 請參閱  
 <xref:System.Attribute>   
 [不在組建中：Visual Basic 屬性概觀](http://msdn.microsoft.com/zh-tw/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)   
 [Inherits Statement](../Topic/Inherits%20Statement.md)