---
title: "屬性不可為泛型或巢狀在泛型內的類型 | Microsoft Docs"
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
  - "bc32067"
  - "vbc32067"
helpviewer_keywords: 
  - "BC32067"
ms.assetid: 93ae2848-0a72-4ae5-82a3-32e0a49bb7cd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性不可為泛型或巢狀在泛型內的類型
屬性已宣告為泛型類型或在泛型類型內進行宣告。  
  
 Visual Basic 和 .NET Framework 目前不支援任何屬性和泛型類型組合。 這表示會套用下列限制：  
  
-   屬性不能是泛型類型或在泛型類型內進行宣告。  
  
-   屬性不可以繼承自泛型類別，泛型類別也不可以繼承自屬性。  
  
-   當您套用屬性時，不可以提供下列任何引數：  
  
    -   泛型類型、  
  
    -   建構自泛型類型的類型、  
  
    -   包含類型的類型參數，或  
  
    -   建構自包含類型之類型參數的類型。  
  
 **錯誤 ID︰**BC32067  
  
### 更正這個錯誤  
  
-   如果屬性宣告包含 `Of` 關鍵字和類型參數清單，則加以移除。  
  
-   如果屬性宣告出現在泛型類型內，則將其移至任何泛型類型之外。  
  
## 請參閱  
 <xref:System.Attribute>   
 [不在組建中：Visual Basic 屬性概觀](http://msdn.microsoft.com/zh-tw/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)