---
title: "屬性引數中不允許類型參數或以類型參數建構的類型 | Microsoft Docs"
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
  - "BC32079"
  - "vbc32079"
helpviewer_keywords: 
  - "BC32079"
ms.assetid: 93eb59bd-e7db-4f73-a37f-405a83df48c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性引數中不允許類型參數或以類型參數建構的類型
屬性所套用的引數是類型參數，或是使用類型參數所建構。  
  
 Visual Basic 和 .NET Framework 目前不支援任何屬性和泛型類型組合。 這表示會套用下列限制：  
  
-   屬性不能是泛型類型或在泛型類型內進行宣告。  
  
-   屬性不可以繼承自泛型類別，泛型類別也不可以繼承自屬性。  
  
-   當您套用屬性時，不可以提供下列任何引數：  
  
    -   泛型類型、  
  
    -   建構自泛型類型的類型、  
  
    -   包含類型的類型參數，或  
  
    -   建構自包含類型之類型參數的類型。  
  
 **錯誤 ID：**BC32079  
  
### 更正這個錯誤  
  
-   重新建構提供給屬性的引數，讓它們不包含任何類型參數或從類型參數建構的任何類型。  
  
## 請參閱  
 <xref:System.Attribute>   
 [不在組建中：Visual Basic 屬性概觀](http://msdn.microsoft.com/zh-tw/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)