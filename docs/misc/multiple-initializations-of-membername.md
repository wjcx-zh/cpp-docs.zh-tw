---
title: "&#39;&lt;成員名稱&gt;&#39; 的多個初始設定 | Microsoft Docs"
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
  - "vbc30989"
  - "bc30989"
helpviewer_keywords: 
  - "BC30989"
ms.assetid: 574b6398-1e9d-43e1-ac16-6fc8687f71d9
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;成員名稱&gt;&#39; 的多個初始設定
'\<成員名稱\>' 的多個初始設定。 欄位和屬性只能在一個物件初始設定式運算式中初始化一次。  
  
 您只能指派一次初始值給物件初始設定式清單中的每個欄位和屬性。 下列宣告無效。  
  
```  
' Dim cust = New Customer() With {.Name = "Bob", .Name = "Robert"}  
```  
  
> [!NOTE]
>  您可以使用一個欄位或屬性作為另一個成員的初始值，如下列宣告所示。  
  
```  
Dim cust = New Customer() With {.First = "Mike", .Last = "Nash", _ .Full = .First & " " & .Last}  
```  
  
 **錯誤 ID︰**BC30989  
  
### 更正這個錯誤  
  
-   請排除物件初始設定式清單中每個欄位或屬性的所有初始設定，只留下一個。  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [不在組建中：屬性程序與欄位](http://msdn.microsoft.com/zh-tw/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)