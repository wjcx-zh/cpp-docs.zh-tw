---
title: "無法初始化展開的屬性 | Microsoft Docs"
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
  - "vbc36714"
  - "bc36714"
helpviewer_keywords: 
  - "BC36714"
ms.assetid: ba9408f3-e606-4749-8372-987999f405f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法初始化展開的屬性
您可以將自動實作的屬性當做其宣告的一部分來初始化，但無法初始化展開的屬性。  
  
 **錯誤 ID︰**BC36714  
  
### 更正這個錯誤  
  
-   使用自動實作的屬性，或從屬性宣告中移除初始化。  
  
## 範例  
 下列範例會顯示自動實作的屬性和展開的屬性。 您可以使用指派或 `New` 子句來初始化自動實作的屬性，但無法初始化展開的屬性。  
  
```vb#  
Class AutoImplementedExample ' An auto-implemented property can be assigned an initial value. Property IDNum As Integer = 33542 ' An auto-implemented property can be initialized with New. Property Name As New String("Don Hall") End Class Class ExpandedExample ' Attempting to expand an initialized auto-implemented property ' causes this error. 'Property IDNum As Integer = 33542 '    Get '    End Get '    Set(ByVal value As Integer) '    End Set 'End Property ' Instead, you can assign the initial value to the backing field. Private _IDNum As Integer = 33542 Property IDNum As Integer Get End Get Set(ByVal value As Integer) End Set End Property End Class  
```  
  
## 請參閱  
 [Auto\-Implemented Properties](../Topic/Auto-Implemented%20Properties%20\(Visual%20Basic\).md)   
 [How to: Create a Property](../Topic/How%20to:%20Create%20a%20Property%20\(Visual%20Basic\).md)   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)