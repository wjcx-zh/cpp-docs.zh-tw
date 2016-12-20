---
title: "&#39;Set&#39; 參數必須和包含的屬性具有相同的類型 | Microsoft Docs"
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
  - "vbc31064"
  - "bc31064"
helpviewer_keywords: 
  - "BC31064"
ms.assetid: f0b8310d-68a1-4989-ac64-03b1861528ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Set&#39; 參數必須和包含的屬性具有相同的類型
`Set` 屬性程序的參數類型與它所屬之屬性的類型不同。  
  
 **錯誤 ID︰**BC31064  
  
### 更正這個錯誤  
  
-   請將參數的資料類型變更為 `Set`，使其符合屬性的資料類型。 例如:  
  
    ```  
    Class Class1 ' Declare a local variable to hold the property value. Private Fval As Integer Property F() As Integer Get Return Fval End Get Set(ByVal Value As Integer) Fval = Value End Set End Property End Class  
    ```  
  
## 請參閱  
 [不在組建中：如何：將欄位和屬性加入類別中](http://msdn.microsoft.com/zh-tw/ae53f61b-3abc-413e-8931-703c5f5e8fc2)   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [不在組建中：屬性和屬性程序](http://msdn.microsoft.com/zh-tw/23e2a1ec-7e9d-4109-8940-c703d981077b)