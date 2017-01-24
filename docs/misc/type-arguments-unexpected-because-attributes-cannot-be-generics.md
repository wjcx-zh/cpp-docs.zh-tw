---
title: "未預期的類型引數，因為屬性不可以是泛型 | Microsoft Docs"
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
  - "bc32066"
  - "vbc32066"
helpviewer_keywords: 
  - "BC32066"
ms.assetid: cd43a92c-33fb-4def-bbf7-527d21bff93c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未預期的類型引數，因為屬性不可以是泛型
屬性是使用類型引數清單所套用。  
  
 Visual Basic 和 .NET Framework 目前不支援任何屬性和泛型類型組合。 這表示會套用下列限制：  
  
-   屬性不能是泛型類型或在泛型類型內進行宣告。  
  
-   屬性不可以繼承自泛型類別，泛型類別也不可以繼承自屬性。  
  
-   當您套用屬性時，不可以提供下列任何引數：  
  
    -   泛型類型、  
  
    -   建構自泛型類型的類型、  
  
    -   包含類型的類型參數，或  
  
    -   建構自包含類型之類型參數的類型。  
  
 **錯誤 ID︰**BC32066  
  
### 更正這個錯誤  
  
-   如果類型引數是要作為正常引數，則請移除 `Of` 關鍵字。 這樣做會將類型引數清單轉換成正常引數清單。  
  
-   如果類型引數是要提供給類型參數，則請移除 `Of` 關鍵字和所有類型引數。 屬性不能接受類型引數。  
  
## 請參閱  
 <xref:System.Attribute>   
 [不在組建中：Visual Basic 屬性概觀](http://msdn.microsoft.com/zh-tw/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)