---
title: "成員 &#39;&lt;成員名稱&gt;&#39; 無法在物件初始設定式運算式中初始化，因為它是共用的 | Microsoft Docs"
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
  - "bc30991"
  - "vbc30991"
helpviewer_keywords: 
  - "BC30991"
ms.assetid: 47e832b4-47e3-426e-b88c-5d5568102fde
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 成員 &#39;&lt;成員名稱&gt;&#39; 無法在物件初始設定式運算式中初始化，因為它是共用的
物件初始設定式無法用來初始化宣告為共用之類別的任何成員。 如需詳細資訊，請參閱[Shared](../Topic/Shared%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC30991  
  
### 更正這個錯誤  
  
1.  檢查類別定義，以判斷哪一個成員為共用。  
  
2.  從物件初始設定式清單中，排除該成員的初始化。  
  
## 範例  
 在下列範例中，`totalCustomers` 是共用成員。  
  
```  
Public Class Customer Public Shared totalCustomers As Integer ' Other declarations and method definitions. End Class  
```  
  
 因為 `totalCustomers` 為共用，所以嘗試在物件初始設定式清單中設定其初始值會導致這個錯誤。  
  
```  
' This declaration is not valid. ' Dim cust As New Customer With { .Name = "Coho Winery", _ '                                 .totalCustomers = 21 }  
```  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)   
 [不在組建中：Visual Basic 中的共用成員](http://msdn.microsoft.com/zh-tw/dbc3783f-83a2-4225-995d-c2d6d025663d)